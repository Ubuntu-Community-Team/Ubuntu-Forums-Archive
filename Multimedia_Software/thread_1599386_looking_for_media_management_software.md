---
title: "looking for media management software"
date: 2010-10-17
forum: Multimedia Software
---

### Post by CitizenErased on 2010-10-17
hey

i'd be looking for a software like the windows explorer on xp, i enter a directory full of mpegs, avis, divx, mp3s, jpegs, ... and get the fileattributes like bitrate, resolution, codec, ... a column for each

with nautilus 2.28.1 i only get very basic info, like size, type, date modified

does anyone know of plugins for nautilus to use it as a multimedia management software or do you have any other suggestions what to use?

thanks in advance, peter

edit: oh and i tried banshee, thats really nice, only thing missing is the resolution

---

### Post by lykeion on 2010-10-17
There could be some nautilus plugins for this, I don't know because I don't use nautilus.
Howevere, there's a program called **mediainfo** that will display a lot of info about media files. You can find it here: [http://mediainfo.sourceforge.net](http://mediainfo.sourceforge.net)
Go to the download page and get the debs for libzen0, libmediainfo0 and mediainfo-gui and install them in that order. 
Note: you need to manually check the page for updates (once every other month or so), since the PPA repo is outdated and doesn't seem to get updated  very often.

---

### Post by CitizenErased on 2010-10-17
> **lykeion said:**
> There could be some nautilus plugins for this, I don't know because I don't use nautilus.
Howevere, there's a program called **mediainfo** that will display a lot of info about media files. You can find it here: [http://mediainfo.sourceforge.net](http://mediainfo.sourceforge.net)
Go to the download page and get the debs for libzen0, libmediainfo0 and mediainfo-gui and install them in that order. 
Note: you need to manually check the page for updates (once every other month or so), since the PPA repo is outdated and doesn't seem to get updated  very often.
just tried that, thats nice, but its more of an ubuntu version of gspot, does what i want, but shows only one file at a time, i want the info mediainfo gives, but in columns for a chosen directory
take for example a folder with 200 mp3s and you want to get rid of all with a bitrate below 128kbit, or a folder with pics and you want to delete all with a resolution less than 1024x768 ...

---

### Post by lykeion on 2010-10-18
Found this thread: [http://ubuntuforums.org/showthread.php?t=878683](http://ubuntuforums.org/showthread.php?t=878683)

It might be a bit more work than just install an app though.
Here's a quick walkthrough (credit goes to [geb666]("http://ubuntuforums.org/member.php?u=637335"))

1. install dependencies
```
sudo apt-get install python-nautilus python-mutagen
```
2. add python-nautilus path to PYTHONPATH
```
gedit ~/.bashrc
```
add this line
[PHP]export PYTHONPATH=$PYTHONPATH:/usr/lib/nautilus-python[/PHP]
save and exit gedit, then update .bashrc
```
source ~/.bashrc
```
3. create the dir and the script
```
mkdir ~/.nautilus/python-extensions
```
```
gedit ~/.nautilus/python-extensions/bsc.py
```
copy and paste from original thread (make sure to replace 8 spaces with tab)
save and exit gedit, then make script executable
```
chmod u+x ~/.nautilus/python-extensions/bsc.py
```
4. restart nautilus
```
killall nautilus
```
5. add artist/album/bitrate columns in list view in nautilus
start nautilus
view > list
view > visible columns... > check Album, Artist, Bitrate
(or set visible columns permanently)
edit > preferences > list columns tab

---

### Post by CitizenErased on 2010-10-24
thanks a lot! thats pretty good!

---

