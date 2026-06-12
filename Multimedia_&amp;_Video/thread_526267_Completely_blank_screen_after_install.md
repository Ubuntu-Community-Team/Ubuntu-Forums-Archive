---
title: "Completely blank screen after install"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by designer17 on 2007-08-15
I am attempting to convert my old desktop into a HTPC but am having a rather frustrating and difficult time.

My goal was to install linux mint on my system but the live cd wouldn't load.  It would go as far as the options menu but once anything was selected the splash screen would load, get to 100% and the sceen would go completely blank and I'd get the generic saying across my screen "no video input" or something like that.  So I figured I'd try the regular Ubuntu 7.04 Live Cd even though I already had a good idea what the predicted outcome was going to be, linux mint is just a spinoff of ubuntu therefore I got the same results.

Searching for my Ubuntu alternative cd, I was going to try and install with that, unfortunately alls I could find was my Ubuntu Studio alternative cd, so I tried installing that with intentions of not installing all the extra studio stuff compiled with the cd.  The installation took a few tries but finally I got it to go through (I think my cd-rom is on its last leg).

So the installation finished, the computer restarted, the splash screen came up and again I got that Damn blank screen saying "no video input".

I have tried booting with my 15" lcd monitor and my 20" lcd tv and got the same results.

After doing some research I figured out its an issue with my NVIDIA card.  I also found a post on how to get the live cd to boot. I followed the directions to a "T" and didn't have any luck.


I am about ready to pull my hair out.  I cannot seem to get to the terminal from the current installed os, nothing seems to work. Any help would be greatly appreciated. Thanks in advance.



SPECS:
Custom built
2.8ghz processor
1gb ram
128mb Geforce 5200 video card

---

### Post by Steve1961 on 2007-08-15
Probably not what you want to hear, but have you tried an alternative live CD such as damn small linux (only a 50 mb download).  Try booting with this and then mount your ubuntu partition and edit /etc/X11/xorg.conf  Change the video driver from nv to vesa and try rebooting.

---

### Post by dabl on 2007-08-15
This may or may not be helpful: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:)

---

### Post by designer17 on 2007-08-15
Thanks dabl and steve for the quick responses.  I will give both these ideas a try and post my results.  At this point I don't care how I get it working just as long as it works.  I most likely won't be able to get to it until tomorrow night, unless I can sneak away from the gf for an hour or so, lol.

---

### Post by designer17 on 2007-08-20
I haven't had much free time but last night I download dsl linux and burnt it to a disc them boot my machine with it.  It booted up and displayed fine but I can't figure out how to get to my xorg file in order to edit it.  I managed to get the hard drive mounted but thats it.

How can I edit my xorg file using dsl?

Thanks

---

### Post by Steve1961 on 2007-08-20
Find out where the mount point of your drive is by entering the command

cat /etc/mtab

e.g. it could be /mnt/hda1 or whatever DSL uses for mount points

Whatever it is the command to get to your xorg.conf should include the mount point followed by the path to xorg.conf.  You might also have to work with the vi editor:

vi /mnt/hda1/etc/X11/xorg.conf

---

### Post by designer17 on 2007-08-20
Thanks Steve. I'll give that a try when I get home.

---

### Post by designer17 on 2007-08-20
First of all I want to thank you all for the help.  Super fast response time.

I managed to figure out the problem which was very weird if I might add.

I booted up dsl and tried editing the xorg file using vi but it wouldn't let me change anything in it.  So I ended up using nano.  I got into the file and my driver was already set to read "versa".  I found this sort of odd and figured for I'd try using the "nv" driver for the heck of it.  Well I rebooted and everything came up perfectly.

So again thanks for the help.

---

