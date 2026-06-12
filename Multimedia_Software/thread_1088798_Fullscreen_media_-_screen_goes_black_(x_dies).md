---
title: "Fullscreen media - screen goes black (x dies?)"
date: 2009-03-06
forum: Multimedia Software
---

### Post by joeri_83 on 2009-03-06
Hi,

I'm having some trouble watching videos on fullscreen. What happens is that after a while the screen goes black, but the sound is still on. It occurs both while watching mpeg files in VLC and when streaming flash videos (although not all the time).

If I use ctrl+alt+f3 (or any other function key) it displays the console. If I use ctrl+alt+backspace to restart x (is that what happens?), I can see the console print outs, but the screen goes black again when the login window should be painted to the screen.

The only way I can get the picture back in X is to restart the computer.

I'm running Ubuntu on an EEE Box, if that matters.

Any ideas of what's gone wrong? I've tried googling, but haven't found any issue that appears to be the same.

---

### Post by joeri_83 on 2009-03-08
Is there any other information that might be helpful?

Happened today as well, although now it froze with the whole screen getting a beige colour, rather than black.

---

### Post by grahamrb on 2009-03-19
I'm having the exact same problem. System seems to run fine all day if you leave it alone but when I start watching a movie or TV show on it (I've tried using VLC, XBMC and the default ubuntu player - can't remember what it's called).

I had a quick look in the xorg log file and the only intresting line I saw was:
(EE) intel(0): underrun on pipe A!


Anyone have any suggestions?

I also have an eeeBox which runs one of the Intel GMA 950 graphics. ([http://en.wikipedia.org/wiki/ASUS_Eee_Box](http://en.wikipedia.org/wiki/ASUS_Eee_Box))


Another edit: found a bug with a similar error to above: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/260933](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/260933)

Another edit: Found a bug which is being more actively looked at: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221119](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221119)

---

