---
title: "Upgraded to 9.04 - All media players crash on startup."
date: 2009-05-03
forum: Multimedia Software
---

### Post by acroporas on 2009-05-03
After upgrading to 9.04 I can no longer play any movies.

Both mplayer and xine crash immediately when I try to play a .avi  Both programs worked fine before the upgrade.

When I run Mplayer from the command line, I get:

X11 error: BadAlloc (insufficient resources for operation)1.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 2 0 
....
X11 error: BadAlloc (insufficient resources for operation)1.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 2 0 


Computer: Emachines T3990
OS: Ubuntu 9.04

---

### Post by Leetbumble on 2009-05-03
I had the same problem I found another post with this [Link.]("http://www.my-guides.net/en/content/view/158/26/#ubuntu_dvd_playback")

Hope this helps.

Ubuntu's only flaw is when something changes in the OS it sometimes takes some work to untangle things. In windows it is simple just give up on your feature, or buy a mac where you have no choices.

If you still need help let me know

---

### Post by acroporas on 2009-05-03
Thanks for responding, but I did not find anything it that link helpful.  Just listed some programs that people find useful.  Nothing about programs crashing.

---

### Post by acroporas on 2009-05-04
Bump.

---

### Post by acroporas on 2009-05-04
Bump again

---

### Post by acroporas on 2009-05-04
Please, can anyone help me?

---

### Post by druggo on 2009-05-06
I have the same error, mplayer give me X11 error: BadAlloc (insufficient resources for operation)

its a myth 9.04 box, with the "intel" driver in xorg.conf... worked flawless in 8.10, please help right now im without a TV :/

apparantly, this has to do with bug [#371275]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/371275")

make sure check your xorg.0.log to see if you get a failed to pin xv buffer, and help by providing info on the bug.

---

### Post by placidoaps on 2009-05-28
Hi, same problem here.

For a work around I use vlc.
To use it you will have to change the video output to X11.

Tools - Preferences - Video (tab) - Output - Video Output X11 (dropdown)

My VLC is in portuguese, I hope I get my translation right!

You can change this parameter in gmplayer too (write gmplayer in a terminal)
You can change this parameter totem too (write gstreamer-preferences in a terminal)

---

### Post by northerndude81 on 2009-05-31
I had the same problem and the above fixed it for me.  Thanks!

---

