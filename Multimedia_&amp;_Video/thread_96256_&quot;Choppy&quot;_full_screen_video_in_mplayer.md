---
title: "&quot;Choppy&quot; full screen video in mplayer"
date: 2005-11-28
forum: Multimedia &amp; Video
---

### Post by renzokuken on 2005-11-28
ok, first off,

im running breezy on a AMD64 3500+, 512mb ram, ATI Radeon 9200SE

when i watch movies and video in general through mplayer the playback is fine in small mode and double size, but as soon as i go to full screen, the quality deteriotes slightly, but enough to get annoying.

what actualy happens is the pictures "shears" during fast moving sequences. imagine having a photo, cutting it into two with a straight cut and putting it back together slightly 'off' from perfect and thats what my full screen video looks like

i installed the fglrx drivers thanks a great guide in these forums a while ago.

i have no idea where to start to solve this problem so any help would be heavily appreciated.

also, i read around a bit and dunno if this helps but:

$ xvinfo
X-Video Extension Version 2.2
screen #0
no adapters present

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

---

### Post by docomo on 2005-11-29
According to xvinfo, xv is not working. Thus, you get non accelerated fullscreen video which is probably the cause of your problem. You probably need to change something in /etc/X11/xorg.conf

Specifically, check under Section "Device" in xorg.conf if you have the lines:

Option         "VideoOverlay"         "on"
Option         "OpenGLOverlay"     "off"

If not, then add them. (Backup the original xorg.conf first.)

Then restart the x server. (press ctrl + alt + backspace)

See this thread for an example of an xorg.conf:
[http://www.ubuntuforums.org/showthread.php?t=24557]("http://www.ubuntuforums.org/showthread.php?t=24557")

---

### Post by renzokuken on 2005-11-29
wow......ur a freaking genius dude !!!!

problem solved and seems to have all round sharpened the video up. 

thanks mucho docomo

---

