---
title: "no sound ubuntu 7.10 nVidia Corporation MCP55"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by heiari on 2007-12-27
hey folks,
I had problem with sound on Kubuntu 7,10 . Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2).
After installation sound worked but at some point no sound. 
Reason was that no alsa driver found ( aplay -l  and  on the other hand integrated  soundcard was found; lspci -v ) . I tried follow  this guide [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) ,  Comprehensive Sound Problem Solutions Guide v0.5e compiled and installed but still no sound. Then i found this post  [http://www.ubuntu-forum.de/artikel/26186/geloest-procasoundcards---ordner-nicht-auffindbar.html](http://www.ubuntu-forum.de/artikel/26186/geloest-procasoundcards---ordner-nicht-auffindbar.html)
...
 Ein einfaches
apt-get install linux-ubuntu-modules-2.6.22-14-386
hat das Problem gelöst....

and got a vo'laa,  at the boot some how the menu.lst had changed boot order and the first one was 
 Ubuntu 7.10, kernel 2.6.22-14-server

I changed to this one:
  Ubuntu 7.10, kernel 2.6.22-14-generic

booted and what a nice sound one can hear.  The learning lesson was- reason can be anything :)

---

### Post by terminal on 2007-12-27
try 
sudo modprobe snd_hda_intel .

Do you know what is ur driver name shown in windows device manager ?

---

### Post by kraizeg on 2008-03-17
thx at all same problem, same bug, same solution. thx all

---

