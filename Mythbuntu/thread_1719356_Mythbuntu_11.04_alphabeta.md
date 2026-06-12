---
title: "Mythbuntu 11.04 alpha/beta"
date: 2011-04-01
forum: Mythbuntu
---

### Post by agamotto on 2011-04-01
Has anyone out there been playing with either flavor of the 11.04 Mythbuntu?  I am curious to know what significant changes are in order, along with whether or not simply PLAYING a cd, and making a DVD out of recordings will finally become an easy task...

---

### Post by nickrout on 2011-04-01
natty currently boasts mythtv 0.24.0+fixes.20110322.c2baf1b-0ubuntu2 which is in fact LESS recent than mythbuntu repos will get you.

---

### Post by gator on 2011-04-03
Logged in with VNC. Opened terminal:

sudo update-manager -d

followed instructions.
The installer asks if you want to replace files that you may have changed, like smb.conf. Do what you have to.
The installer cleaned up and rebooted.
Slower than normal bootup as my drives got a workout being scanned(?).
On reboot it  couldnt find backend. I confirmed my settings by doing nothing next..next..next..Asked me if i would like to upgrade my database...**** yeah.
The frontend started with a different theme than before but was easy to change, there's even a new menu item for changing theme's.

My ms remote was jumping two menu options with each press. Fixed it with this link.  [http://www.pcmediacenter.com.au/forum/topic/43146-solved-mce-remote-issues-multiple-keypresses/](http://www.pcmediacenter.com.au/forum/topic/43146-solved-mce-remote-issues-multiple-keypresses/)

The UI is more responsive.
 
So everything is good for me, except for the minor remote problem.

VDPAU with HDMI audio on a GT220.
Filesystems:
OS = ext4
LiveTV + movies + blurays = XFS
blurays + movies = BTRFS

---

### Post by ttucker on 2011-05-01
Gator, 

I just updated to the 11.04 version and am having the same problems with my MS MCE remote.. I went to the link you mentioned, and noticed several different possible solutions.  I was wondering which one you used to fix this.

Thanks in advance.

---

