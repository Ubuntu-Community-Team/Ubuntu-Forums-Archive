---
title: "Help needed with i810e graphics issues."
date: 2008-12-13
forum: Multimedia Software
---

### Post by swr12 on 2008-12-13
Hi,

I am looking for some advice about the graphics issues I am having on my computer. I have been trying to figure this out for a while, and have looked it up on countless forums including this one. The first problem I am experiencing is when my computer is using hardware acceleration to draw a certain graphic and I rest my mouse over the said graphic a square forms around the mouse where that part of the graphic stops being refreshed. This causes ugly squares to be left on the menus when I am using special effects. I am able to get the squares to stop showing up by disabling hardware acceleration, but I would like to use acceleration since it improves 3d graphics rendering quite a bit. Another problem I am having is when I turn on special effects the title bars and window borders disappear to all the windows. I have taken a screen shot to show both the first and second problem. I think this problem has something to do with the wobbly windows. With Ubuntu 8.04 the normal special effects work fine except for the cursor squares. With Ubuntu 8.10 the wobbly windows are enabled with the normal special effects and my bars and borders are MIA. I am not sure why the wobbly window effect wouldn't work though since I used them with this computer before on a different Linux distribution. A possibly related problem I am having is that the DDC/EDID is not working correctly on my computer forcing me to have to manually put in the monitor specs. With one of my monitors I must disable the DDC or all the 3d rendered graphics just show up as garbage on the screen. With my other monitor, which is an LCD, reading the EDID fails altogether.

This is part of the xorg log with my LCD screen:
```
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level none
(II) intel(0): VESA VBE DDC transfer in appr. 0 sec.
(II) intel(0): VESA VBE DDC read failed
```

As you can see my computer has Intel graphics. The Intel i810e to be specific.

Any advice would be immensely appreciated.

---

### Post by swr12 on 2008-12-13
Sorry,

I forgot the screen shot. Here it is.

---

### Post by swr12 on 2008-12-13
Hello?

---

### Post by swr12 on 2008-12-13
Can anyone out there help me?

---

### Post by falcon61102 on 2008-12-13
First, by bumping as much as you have recently it actually looks like people are responding to your posts so some may not be as apt to look at your thread.

Second, it looks like the Intel chipset is using the VESA driver which is more like a backup driver.  Have you checked to ensure the correct drivers are installed?  Also, what's the outpout to:
```
sudo lshw -C display
```

---

### Post by swr12 on 2008-12-13
I am not sure how to check whether the driver is installed correctly. I thought that x.org automatically detects what driver to use. I think that it is using the Intel driver. The following shows up in xorg log file:

```
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
```

The command you asked me to run outputs this:

```
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82810E DC-133 (CGC) Chipset Graphics Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

---

### Post by falcon61102 on 2008-12-13
Alright, it doesn't look like you have a driver installed for you card.  Try going to System>Administration>Hardware Drivers and seeing if it needs any restricted drivers to work.  If if is listed, enable it and it should install.  If it's not listed, post back and we'll find the right drivers and get them installed.

---

### Post by swr12 on 2008-12-13
when I go to Hardware Drivers their are no drivers listed to enable, and at the top it says that no proprietary drivers are in use on this system.

---

### Post by falcon61102 on 2008-12-13
Alright, after some research, I found a possible solution.  It seems you need to uninstall the old drivers and install new.

Copied from: [http://ubuntuforums.org/showthread.php?t=975990&highlight=i810e&page=3](http://ubuntuforums.org/showthread.php?t=975990&highlight=i810e&page=3)

1. uninstalled xserver-xorg-video-intel
2. installed xserver-xorg-video-i810
3. set driver to "i810"

If you need help completing any of these things let me know.

---

### Post by swr12 on 2008-12-14
I uninstalled the Intel driver with synaptic package manager. Then I went ahead and installed the i810 driver. When I selected the i810 for instillation the package manager also selected the Intel driver for instillation so I deselected it again and it deselected the i810 driver. Evidently their is no way to uninstall the Intel driver and keep the i810 driver. So I went ahead and configured xorg to use the i810 driver then loged out. When the login screen should have popped up the screen just stayed black. So I rebooted and the same thing happened again. So I rebooted again and chose the second option in grub. I then selected xfix. Then I continued on booting. Now I am back to square one. Did I do anything wrong?

---

### Post by falcon61102 on 2008-12-14
Doesn't sound like you did anything wrong, it just may not have worked as we would have liked.  Ok, well at least you have the correct driver now.  Next I would look at Compiz and either disable it or remove it at least temporarily to test if it is causing your problems.  If you boot to the recovery mode and open up the terminal, you can use the following to remove compiz:
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

Compiz has been causing a few people problems lately and a surefire way to test if it is the culprit would be to remove it and try booting.  If you can successfully boot, then we'll go about trying to get compiz back in a working order.

---

### Post by swr12 on 2008-12-14
OK, I have removed compiz-fusion. As you might predict special effects are not working. The square around the cursor is still appearing. DDC is still not working correctly.

---

### Post by falcon61102 on 2008-12-14
Well considering you've tried new graphics drivers and removing Compiz, I going to go with it being a problem with GNOME itself.  Could be the theme/window manager or even the cursor.  Have you tried using a different theme or cursor to see if the problem carries over?

---

### Post by swr12 on 2008-12-14
I'm not sure how to change the cursor, but I did change themes to no avail. I think that the square around the cursor has to do with driver since the square only appears when hardware acceleration is enabled. If I set noaccel to true in xorg.conf the mouse doesn't have any squares around it ever. I would like to have hardware acceleration enabled though.

---

### Post by leoh on 2010-04-21
I am having exactly the same issue with exactly the same video card (intel 82810e). I have tried both Ubuntu 9.04 and 9.10, and both give me the same result.
Is there anything else I can do?

---

