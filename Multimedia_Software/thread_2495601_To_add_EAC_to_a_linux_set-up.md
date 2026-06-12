---
title: "To add EAC to a linux set-up"
date: 2024-02-24
forum: Multimedia Software
---

### Post by shantiq on 2024-02-24
had not done this for a while so had to learn again; may be of use


To add [EAC]("https://www.exactaudiocopy.de/") to a linux set-up ---    this tested on Ubuntu and Manjaro [Feb 2024]


Install Wine
-------


&#10122; Install Wine and if your version of Wine does not have 32-bit do this 


1) Open up the terminal by pressing Ctrl + Alt + T. And type the following commands:
   ```
cd ~
   rm -rf .wine
   rm -f .config/menus/applications-merged/wine*
   rm -rf .local/share/applications/wine
   rm -f .local/share/desktop-directories/wine*
   rm -f .local/share/icons/????_*.xpm 

```

   2) Now to set your environment variable and also to create your new 32-bit WINEPREFIX go ahead and type:




```
   WINEARCH=win32 WINEPREFIX=~/.wine winecfg



```&#10123; you will need this for EAC


```
winetricks -q dotnet20



```let this install


&#10124; install [EAC]("https://www.exactaudiocopy.de/eac-1.6.exe")


======


if you have troubleshooting issues refer to the older thread [page 1]("https://ubuntuforums.org/showthread.php?t=2092214")


======


if you wish for a perfect rip use this info here from a now defunct site


[[IMG]https://i.postimg.cc/qhLgqwjV/1.png[/IMG]]("https://postimg.cc/qhLgqwjV")[[IMG]https://i.postimg.cc/1V3XqFjg/2.png[/IMG]]("https://postimg.cc/1V3XqFjg")[[IMG]https://i.postimg.cc/MX9v8sn1/3.png[/IMG]]("https://postimg.cc/MX9v8sn1")[[IMG]https://i.postimg.cc/nMFCg8hH/4.png[/IMG]]("https://postimg.cc/nMFCg8hH")

---

### Post by karimoui on 2024-04-13
[COLOR=#0F0F0F][FONT=Roboto]bro thank you so much, i&#8217;ve been trying to get dead by daylight working on my steam deck for so long and now it does!



[/FONT][/COLOR]

---

