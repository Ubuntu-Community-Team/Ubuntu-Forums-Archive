---
title: "Steam Left 4 Dead 2 demo installation hellp!"
date: 2009-11-28
forum: Multimedia Software
---

### Post by blada4life on 2009-11-28
so i downloaded wine, and installed steam. everything is fine so far. then i downloaded the Left 4 Dead 2 Demo. it gets to 100%. at this point i am pumpeed. but then i try to instal it and i get an error message as so:
[IMG]http://i880.photobucket.com/albums/ac6/maximumax1/Screenshot-Steam-Error.png[/IMG]



help  me? im new to ubuntu so im prolly going to need step by step directions.thanks

---

### Post by ikacer on 2009-11-28
from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18233]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18233"):

- To get past the "Incomplete Installation (2)" error:

Upgrade to Wine 1.1.33 or later.  If using an old version of Wine, you can continue to use these old instructions:

1. Install the L4D2 demo using Steam
2. Quit Steam
3. Download this gzipped tarball (~14 MB):
   [http://www.tghost.co.uk/wine/steamappscommon.tar.gz](http://www.tghost.co.uk/wine/steamappscommon.tar.gz)
4. Extract that into the steamapps/ directory:
   ~ $ wget [http://www.tghost.co.uk/wine/steamappscommon.tar.gz](http://www.tghost.co.uk/wine/steamappscommon.tar.gz)
   ~ $ cd .wine/drive_c/Program\ Files/Steam/steamapps/
   steamapps $ tar -xvf ~/steamappscommon.tar.gz
   This will overwrite a few existing files, create some new directories, and create some new files, all inside the steamapps/common/left\ 4\ dead\ 2\ demo/ directory.
5. Launch the game using Steam

This broke again after a Steam patch, but re-extracting the archive fixes it again.

--------

so try updating WINE. Here is info on how to do that. [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

---

### Post by blada4life on 2009-11-28
wait what do i do after i extract it to the directory?

---

### Post by ikacer on 2009-11-28
try updating wine first. Version 1.1.33 and newer are reported to work. Take a look at the last line of my previous post if you are unsure how to get the newer version of wine.

---

### Post by blada4life on 2009-11-28
but by reinstallin 1.1.33 wont i have to install and download everythin all over again?

---

### Post by ikacer on 2009-11-28
> **blada4life said:**
> but by reinstallin 1.1.33 wont i have to install and download everythin all over again?

all your steam files are stored in ~/.wine
they wont be lost if you update to a newer version.

---

### Post by ikacer on 2009-11-28
> **blada4life said:**
> but by reinstallin 1.1.33 wont i have to install and download everythin all over again?

all your steam files are stored in ~/.wine
they wont be lost if you update to a newer version.

EDIT: after you add ppa:ubuntu-wine/ppa to your software sources you just have to open up the update manager and update your system.

2nd EDIT: oops double post

---

### Post by blada4life on 2009-11-28
you my friend, are the best

but now i got a new problem. i got past the installation problem, i got to the play game button. clicked on it. haha the game is popping up :/

---

### Post by ikacer on 2009-11-28
> **blada4life said:**
> you my friend, are the best

but now i got a new problem. i got past the installation problem, i got to the play game button. clicked on it. haha the game is popping up :/

Is it working now?

Looking at the wine appdb, it looks like there is also a problem with getting multiplayer to work. If you have troubles with multiplayer, add urlmon.dll in the library tab of your wine configuration.

---

### Post by blada4life on 2009-11-28
still no good

---

### Post by blada4life on 2009-11-28
i think my problem is that i didnt properly instal the newest wine. im doing that right now. ill check up and tell you the status after

---

### Post by ikacer on 2009-11-28
does it give any error messages? try running it in a terminal:
```
wine "left4dead2.exe"
```
I'm not sure if left4dead2.exe is the program name, I'm just guessing here, so you may have to change that part. Also you will have to navigate to the file location before running this command. (tab completion is you friend)

hopefully this will post some sort of output in the terminal when it freezes-up (or crashes?) and you can post that output here.

---

### Post by ikacer on 2009-11-28
> **blada4life said:**
> i think my problem is that i didnt properly instal the newest wine. im doing that right now. ill check up and tell you the status after

if you go to
Applications -> Wine -> Configure Wine
in the 'about' tab it has the version number.

---

### Post by blada4life on 2009-11-28
wine client error:0: version mismatch 0/393.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

---

### Post by ikacer on 2009-11-28
> **blada4life said:**
> wine client error:0: version mismatch 0/393.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

if an instance of wine is still running, you can kill it by opening up a terminal and typing:
```
killall wine
```
although, my guess is that it's not the problem.

How did you go about updating wine?

---

### Post by blada4life on 2009-11-28
good news. i have wine 1.1.33. bad news:
[IMG]http://i880.photobucket.com/albums/ac6/maximumax1/Screenshot-Error.png[/IMG]

---

### Post by blada4life on 2009-11-28
how did i update wine? i went to the ubuntu software center and downloaded the wine binary beta (or wine 1.1.33)

---

### Post by ikacer on 2009-11-28
> **blaca4life] how did i update wine? i went to the ubuntu software center and downloaded the wine binary beta (or wine 1.1.33) [/QUOTE]
ok, nvm. I guess that's not the problem.

[QUOTE=blada4life said:**
> good news. i have wine 1.1.33. bad news:
[IMG]http://i880.photobucket.com/albums/ac6/maximumax1/Screenshot-Error.png[/IMG]
[https://support.steampowered.com/kb_article.php?ref=2537-DLCV-6627]("https://support.steampowered.com/kb_article.php?ref=2537-DLCV-6627")

Do you have a graphics driver installed?
System -> Administration -> Hardware Drivers

Also, what is your graphics card? Could you run the following command
```
lspci -v
```
in the output there should be a section on 'VGA compatible controller:' or something along those lines. post that section.

---

### Post by blada4life on 2009-11-28
ahaaha oh my god i forgot how terrible this comp was. what a waste of time. hahahaha. thanks a ton for your help though. i couldnt be more grateful.

lmfao, its like a 5 year old conpaq netbook

---

### Post by ikacer on 2009-11-28
> **blada4life said:**
> ahaaha oh my god i forgot how terrible this comp was. what a waste of time. hahahaha. thanks a ton for your help though. i couldnt be more grateful.

lmfao, its like a 5 year old conpaq netbook

Cheers. :)

---

### Post by blada4life on 2009-11-28
i get carried away by how nice ubuntu 9.1 looks XD

---

