---
title: "Screen resolution stuck at 800 x 600"
date: 2009-11-24
forum: Multimedia Software
---

### Post by nanogeek on 2009-11-24
Since upgrading to 8.10 I have had problems with my video display.
I used to have the display set to 1024 x 768, but now it is set to 800 x 600. When I go to System > Preferences > Display > Resolution only 640 x 480 and 800 x 600 appear. At 800 x 600 there is not enough screen real estate to see what I need to.

How can I restore the screeen resolition to 1024 x 768.

I am running a Pentium III (yes 3) with on-board video adapter and an Ipex 17” CRT monitor.
This archaic hardware used to run at 1024 x 768 without a prooblem.

Any suggestions?

TIA
Nanogeek

---

### Post by HappyFeet on 2009-11-24
> **nanogeek said:**
> At 800 x 600 there is not enough screen real estate to see what I need to.


If you do Alt-click on a window, you will be able to drag it around to be able to see the whole window. Sorry I can't be of more help.

---

### Post by AKADAP on 2009-11-24
> **nanogeek said:**
> Since upgrading to 8.10 I have had problems with my video display.
I used to have the display set to 1024 x 768, but now it is set to 800 x 600. When I go to System > Preferences > Display > Resolution only 640 x 480 and 800 x 600 appear. At 800 x 600 there is not enough screen real estate to see what I need to.

How can I restore the screeen resolition to 1024 x 768.

I am running a Pentium III (yes 3) with on-board video adapter and an Ipex 17” CRT monitor.
This archaic hardware used to run at 1024 x 768 without a prooblem.

Any suggestions?

TIA
Nanogeek

This kind of thing usually happens when the computer can't tell what monitor is connected. You don't have the monitor connected via one of those cables that break the VGA signal into 4 or 5 coax cables do you? If you do, the computer can't ask the monitor what its capabilities are. You can work around this by manually telling the computer what the capabilities of the monitor are, but you need to edit some config files.

---

### Post by nanogeek on 2009-11-25
No, it's a plain old VGA connector.
It is true that when I open the Display dialouge box, it says "monitor unknown." How can I tell the OS what the properties of the monitor are?

---

### Post by bablo on 2009-11-25
Maybe a reinstall of your video card drivers might do the job. These kind of problems usually come from missing or bad video drivers.

---

### Post by nanogeek on 2009-11-25
There is no video card. The video adapter is on the motherboard.

---

### Post by bablo on 2009-11-25
> **nanogeek said:**
> There is no video card. The video adapter is on the motherboard.
Still, it needs a correctly installed driver to be able to use the higher resolutions. Try googling for a driver using the name of your chipset, joined with "ubuntu 8.10" or "Linux 2.6.27", since that is the kernel you're running.

---

### Post by nanogeek on 2009-11-25
I have the CPU install disk.
Under "drivers" there are only Windows drivers. No Linux drivers

When I type in Terminal:
lspci | grep VGA

I get
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)

When I Google Intel Video Ubuntu 9.04
I get lots of links to sites that say there is a problem.

Can I resolve this problem.
Is there an easy way to roll back to 8.10 or 8.04?

---

### Post by mörgæs on 2009-11-29
> **nanogeek said:**
> Is there an easy way to roll back to 8.10 or 8.04?

Yes: The easy way is a clean install :-) You can not go backwards in versions otherwise.

Before doing so, it might be worthwhile to take a look at
[http://ubuntuforums.org/showthread.php?t=1333144](http://ubuntuforums.org/showthread.php?t=1333144)

---

