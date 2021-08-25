# LTspice-themes (Win)

Relatively easy way to switch themes on LTspiceXVII on windows once you're all set up.

## Usage

1) Run `LTspice-themes sakabug-dark` in PowerShell while LTspice is closed.
2) Open LTspice, and sakabug-dark theme is active.

![alt text](https://github.com/sakabug/LTspice-themes/blob/main/images/p1.jpg?raw=true)
![alt text](https://github.com/sakabug/LTspice-themes/blob/main/images/p2.jpg?raw=true)
![alt text](https://github.com/sakabug/LTspice-themes/blob/main/images/p3.jpg?raw=true)
![alt text](https://github.com/sakabug/LTspice-themes/blob/main/images/p5.jpg?raw=true)
![alt text](https://github.com/sakabug/LTspice-themes/blob/main/images/p6.jpg?raw=true)

## How do get it work?

1) Check where your LTspiceXVII.ini is located. Probably in \$HOME\appdata\roaming folder.
2) Put included LTspice-themes.txt somewhere of your choosing.
3) Add this to your PowerShell_profile.ps1, or have the function work in your preferable way. NOTE the file paths for the .ini and .txt:

```powershell
### LTspice-themes ###
function LTspice-themes ([string]$theme) {
  $file1 = "$HOME\appdata\roaming\LTspiceXVII.ini"
  $file2 = "$HOME\appdata\roaming\LTspice-themes.txt"
  $content1 = Get-Content -Path $file1
  $content2 = Get-Content -Path $file2
  foreach ($line in $content2){
    if ($line -eq $(-join("[",$theme,"]"))) { $index2 = $content2.IndexOf($line) }
  }
  foreach ($line in $content1){
    if ($line -eq "[Colors]") { $index1 = $content1.IndexOf($line) }
  }
  for ($i=1; $i -lt 36; $i++){
    $content1[$index1+$i] = $content2[$index2+$i]
  }
  $content1 | Set-Content -Path $file1
}
```

4) Restart PowerShell and run `LTspice-themes sakabug-dark` in PowerShell while LTspice is closed.
5) Open LTspice, and sakabug-dark theme is active.

## Adding new themes

1) Open LTspice-themes.txt.
2) Open LTspice and edit color theme to your liking from palette, and **close LTspice**.
3) Open LTspiceXVII.ini and copy paste entire [Colors] section to the LTspice-themes.txt to the end of the file.
4) Still .txt change the newly brought profile's [Colors] line to [theme-name], and save.

### Or
 
2) Copy paste premade [Colors] section from somewhere. Just change the [Colors] to [theme name] and save.

![alt text](https://github.com/sakabug/LTspice-themes/blob/main/images/p4.jpg?raw=true)

## Misc

If you want to share your theme, I can centralize them here.
And sorry, don't have any Mac devices on hand.
