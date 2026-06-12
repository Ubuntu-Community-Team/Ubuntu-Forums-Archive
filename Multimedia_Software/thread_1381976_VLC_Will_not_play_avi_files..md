---
title: "VLC Will not play avi files."
date: 2010-01-15
forum: Multimedia Software
---

### Post by chrispche on 2010-01-15
When I try to run a divx avi I get this:

chrisc@chrisc-desktop:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x9493140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x97ffbb8] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  102
  Current serial number in output stream:  103
Segmentation fault
chrisc@chrisc-desktop:~$ 

What is wrong. I must have VLC working. It worked fine in Fedora 12.

---

### Post by d3v1150m471c on 2010-01-15
use the default movie player. mine plays avi just fine. if it doesn't it will prompt you to download the plugin for it. then close it and open the .avi file with it again.

---

### Post by chrispche on 2010-01-15
I'm not sure what you mean. When I open VLC with an avi it just closes itself again without playing the file. The above information was gained through the terminal.

---

### Post by Cabs21 on 2010-01-15
Did you try running at different video format to make sure VLC is not working.

My VLC works fine but once I accidentally changed a setting and lost video but not audio.  Had to play with the settings in VLC to tell it to use GNOME playback.

---

### Post by chrispche on 2010-01-15
Yes it's sorted now thanks. I changed the video output to openGL. Solved. :D

---

