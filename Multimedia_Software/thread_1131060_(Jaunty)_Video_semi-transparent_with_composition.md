---
title: "(Jaunty) Video semi-transparent with composition"
date: 2009-04-20
forum: Multimedia Software
---

### Post by harimashinji on 2009-04-20
Hello all. I'll get right to the point.

Ahem..(I hope i posted in the right section)

While using Ubuntu 8.10 i used to watch videos via smplayer in either XV or vdpau, with metacity as composition. Everything worked fine. After my upgrade to Jaunty RC however- it doesn't work as fine anymore.

XV has stopped working completely and gives med alot of *X11 error: BadMatch (invalid parameter attributes)* instead. vdpau, gl and gl2 works but the video window becomes semi-transparent and the black borders around the video disappears. This is mostly noted in fullscreen mode since the desktop is visible even though it shouldn't be.

I also noted that virtualbox was affected by this as the virtual envoirment became semi-transparent as well. But when i turn off compiz or xcomp the problem disappears but XV still won't work. And while using xcomp or compiz i can watch video using X11 but the black borders are still missing. I'm using nvidias 180.51 driver on my Geforce 8200.

I've been trying to fix this for a while but i got nothing...so i hope maybe someone else has this problem or similar and can shed some light on it :)

[[img]http://pici.se/thumbs/t_mjHopRyML.gif[/img]](http://pici.se/p/mjHopRyML)

---

### Post by tomgeeza on 2009-04-27
I have the same problem with Jaunty, running a WinXP guest in VirtualBox 2.2.   The guest window is semi-transparent and unusable if other windows are present.  Can work around by switching off Compiz but I'd like to keep this if poss.  I've seen some reports of this on other forums, Intrepid and Jaunty.

I'm a relative newbie, so I'd appreciate help with this.

Are there any fixes in the works?

---

### Post by ouija on 2009-05-03
I am now experiencing the very same issue now that I have upgraded to Jaunty.

Found on another site that running a script is supposed to help (but it didn't for me):

> #!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1 
VBoxManage startvm "Windows XP" 


However, I was having the same "transparency" issue when using Kdenlive as well, and I added the "export XLIB_SKIP_ARGB_VISUALS=1" command to my "kdenlive_start" script and now this has fixed the issue; however I could not get it to work with Virtulbox.

Hopefully there will be a fix for this.

UPDATE:

Got it working by adding the "export XLIB_SKIP_ARGB_VISUALS=1" command to the VirtualBox shell script (found under /bin/VirtualBox) using the command "sudo gedit /bin/Virtualbox" and then pasting the line into the file, near the top.

Hope this helps!

---

### Post by johnboiles on 2009-05-05
Having the same problem in Jaunty and VirtualBox 2.2.2

ouija, I don't have a /bin/VirtualBox but my script is instead at /usr/bin/Virtualbox. Is that what you meant?

I added export XLIB_SKIP_ARGB_VISUALS=1 to /usr/bin/VirtualBox right under the line that reads PATH="/usr/bin:/bin:/usr/sbin:/sbin" but I still get transparency. The wierd thing is the first time I used the VM it worked fine!

Note that when I pause the machine, it's not transparent.

I also tried to turn of 3d acceleration for the VM, no change.

I'm going to restart Ubuntu. I'll let you know how that goes. It's wierd that it worked the first time.

---

### Post by johnboiles on 2009-05-05
I rebooted and now I don't have any problems. I tried to recreate the problem by: turning seamless mode on and off, removing the line ouija suggested from /usr/bin/VirtualBox, restarting the machine several times. But it works now / it's not transparent at all.

If other people are having the same problem, it's surely not a fluke. If I start having trouble again, I'll post.

EDIT: I'd like to point out that the thread creator, harimashinji, created a bug report
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/364764](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/364764)

EDIT: I'd also like to note that I have an ATI video card

---

