---
title: "ati driver update followed by a blank screen"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by beero1000 on 2008-01-02
I recently (yesterday) switched to ubuntu from xp.

I have a ati x700 vidoe card and I updated to the 'fglrx' ati drivers, as per [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

after the reboot, i got my bios screen, then the ubuntu loading screen, then a black screen. my monitor displayed 'Out of Range H -67.0  V +59.9 SEP'. I'm pretty sure that H = horizontal and V = vertical, so its just the video settings, but I have no idea how to fix it.

ctrl+alt+f1 and alt+f1 don't work (still a black screen, I may be inputting stuff, I just can't see it)

I don't see a grub screen so I don't know how to go in to recovery mode.

I've read through the solutions in the sticky thread, but I'm still not sure what I should do. I'm currently working on a live session on the ubuntu cd. I can see my xorg.conf file, but I can't alter it

I'd appreciate any help.

Thanks

---

### Post by erfahren on 2008-01-02
first, let me say this ..... if you're using Gutsy, the ATI proprietary driver (fglrx) included with it is pretty stable. That driver can be enabled by going to System > Administration > Restricted Drivers Manager (it isn't enabled by default) -- if you have an internet connection it will automatically download and install it and should be in use when you reboot. (with that driver you do need to install the xserver-xgl package to enable desktop effects.)

To install the newer driver version from ATI (that doesn't require XGL) this guide is better: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

-- I realize that's not very helpful now, but anyway...


before the Ubuntu loading screen do you see something like this? If so hit ESC and you should see a menu that will let you select the Recovery Mode:

[IMG]http://img145.imageshack.us/img145/8644/pwrecover01fi6.png[/IMG]

boot into the Recovery Mode - it will ask for the root password - enter your user password 
- you'll get the root prompt ( # )

there enter:
```

dpkg-reconfigure -phigh xserver-xorg

```
That will take you through the steps of reconfiguring the X Server (the /etc/X11/xorg.conf file)
(I've never ran that with the "-phigh" option, but it's supposed to make it set the defaults for most of the selections)

When you get to the point to select the video driver take the "ati" one. (the "ati" one is the open-source driver for ATI cards - the "vesa" is the basic default (fallback) driver)

you probably shouldn't try to set the resolutions manually unless you absolutely have to. They should get configured automatically.

once you are done you can reboot from the command line with:
```

shutdown -r now

```

hopefully you'll be able to boot to the GUI then.

---

### Post by irunwithknives on 2008-02-17
I am having the same problem, and when I type 

dpkg-reconfigure -phigh xserver-xorg

it simply says

xserve-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/X11/xorg.conf.20080217124822

---

### Post by erfahren on 2008-02-17
> **irunwithknives said:**
> I am having the same problem, and when I type 

dpkg-reconfigure -phigh xserver-xorg

it simply says

xserve-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/X11/xorg.conf.20080217124822
that statement just means that it is going to create a new xorg.conf file and is backing up the original (and gives its file name). you should be able to press "enter" to go forward - use the tab key to move between selections if needed.

are you doing this from the recovery mode? 

here are a couple guides on it:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
[http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)
[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server)

---

### Post by Jordinho on 2008-02-28
That method worked like a charm for me! Thanks!

---

