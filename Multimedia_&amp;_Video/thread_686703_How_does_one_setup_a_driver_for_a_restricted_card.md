---
title: "How does one setup a driver for a restricted card"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by gwm on 2008-02-03
Hi,
I have a Foxconn motherboard that has a PCI Express video card slot. I installed Gutsy without a video card. From the BIOS, I think the motherboard uses 64Mb of ram and does it's own video generation. Very slow. Google Earth is chunky and adobe flash simply doesn't work. So I bought a video card (NVIDIA GeForce 7200GS DDR2) and installed it. The machine is dual boot and the Windows drivers supplied with the card work just fine.

Perhaps I messed up the driver install in Ububtu  by defining the wrong card or something. Can anyone tell me how to cleanup and start again?

The problem manifests itself differently, depending on the BIOS settings. Windows works fine with both sets of settings.

1. Leave AGP wait states and Direct Frame Buffer (whatever that is) enabled:

Ubuntu starts booting OK, displays the Ubuntu logo and the  progress bar goes all the way across. Then we drop into a tty screen that flashes three times and then sits there staring at me. It echos keystrokes but does no command processing. The tty screen displays some messages. The last two are:
    Checking battery state ... [OK]
    Running local boot scripts (/etc/rc.local) [OK]
When I press the power button briefly, I get:
    *Stopping Gnome Display Manager ...
And the PC shuts down in an orderly fashion.

2. Disable AGP wait states and Direct Frame Buffer:

As before, Ubuntu starts up fine until the progress bar has run it's course. The the screen flashes a few times again but this time it displays the following:
    Starting up
    Loading, please wait ...
    kinit: name_to_dev_t (/dev/hda5) = hda5(3,5)
    kinit: no resume image, doing normal boot ...

    Ubuntu 7.10 puella tty1
    puella login:

I can then login but have no idea what to do next, except logout again.
Commands like ls, dir and sudo reboot work fine. When I reboot, I get the a bunch of shut down messages before the GUI briefly displays the Ubuntu logo again and then switches the power off.

Any help would be vary much appreciated.

:confused:

gwm

---

### Post by alan34 on 2008-02-03
Set your BIOS so you get to the login screen.

Login then type

sudo dpkg-reconfigure -phigh xserver-xorg

a menu will come up, make sure you pick the vesa driver and then

sudo shutdown -r now

Hopefully you should have you proper GUI login screen now

Go System - Adminstration - Restricted Driver Manager and your Nvidia card should
be there, enable the driver and off you go I hope. If it messes up you can always
run the above command again.

Note Ctl-Alt-F2 will get you to a text login screen and Ctl-Alt-F7 will take you back
to the desktop.

Good luck

---

### Post by gwm on 2008-02-04
Thanx alan34,
problem solved.

A note to anyone else using this solution:

When I rebooted the machine, I couldn't get a tty prompt the way I had previously. However, I used alan34's suggestion and pressed **ctl-alt-f2** which gave me another terminal screen (tty2 in this case).

Then when I ran **sudo dpkg-reconfigure -phigh xserver-xorg** no menu was presented to me, only a message about having backed up the old config file.

After that, it all worked fine. I went to **System > administration > restricted drivers manager** and selected the nvidia driver (there seems to be only one universal driver) and restarted again. Now I can do compiz and all that!!!

:guitar::lolflag:

Thanx again to alan34

---

