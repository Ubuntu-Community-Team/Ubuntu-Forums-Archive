---
title: "Hawking USB Network Adapter: Getting it up and running in Ubuntu!"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by PCessna on 2009-01-02
Hey you? Do you have a Hawking USB Network adapter that don't work, or you're thinking it may be a lightweight to linux? STOP IT, It works fine with Linux. This tutorial will give you a breif summary of my experience with the product, and how to get it up and running!

Summary: 
Hawking claims this device only works with Microsoft's operating system, Windows. People claim it works plug-and-play fine with Mac, and with a small download, The following solution seems to cure the I-don't-work blues for all USB Network Adapters from Hawking in general manufactured in the past couple of years. This works PLUG- AND - PLAY WITH FEDORA LINUX! NO DRIVERS NEEDED FOR FEDORA AND MAC. JUST PLUG IN AND REBOOT, OR BOOT WITH IT PLUGGED IN FOR FIRST TIME FOR FEDORA AND MAC OR PLUG AN WAIT A FEW MOMENTS.

This solution works with: ( I WILL NOT KEEP AN UPDATED LIST )
Wireless 108G Wireless USB Network Adapter (Best Buy, 50USD, United States of America) 

The signal range of the pervious built in cheap 40$ PCI express Broadcom gave me 1MB down, 500KB up, and 1-2 bars in signal out of 4 bars.
This new device that was only 10$ more, USB, gave me 3-6 DOWN, and 1.5-2MB UP, and 2-3 BARS signal out of 4 bars. 

It is also speedy. Works with DRIVER installed on Windows, Works with DRIVER installed on Linux, and works plug-and-play with Macintosh. It does not currently have any support for last-but-not-least, Solaris, However, OpenSolaris without-a-doubt it should work, If I test it, I'll let ya'll know. 

HOW DO I GET IT UP AND RUNNING:

Step 1:
Download this compressed folder in-it contains the drivers, it will need to be extracted. 
[http://downloads.sourceforge.net/zd1211/zd1211-firmware-1.4.tar.bz2?modtime=1191498990&big_mirror=0](http://downloads.sourceforge.net/zd1211/zd1211-firmware-1.4.tar.bz2?modtime=1191498990&big_mirror=0)

When extracted, there is one folder, in it containted the drivers.

Make a NEW folder in your home directory called "firmware" move the folder that you got after extracting that folder I told you to download into this firmware folder.

Give old GUI a quick kiss goodbye, You'll miss him for a few moments. Now open terminal.

Each number and : means a new line after the : is to be typed exactly as is in terminal. 
1:cd ~/
2:sudo mv zd1211-firmware /lib/firmware
3:exit
Done!

If you want to use a newer future version of the driver, disable networking, login and out and do the following in terminal:
1:gksudo nautilus
(if not GNOME / Ubuntu)
1b:sudo nautilus

Now, navigate to /lib/firmware
find the driver you want to kiss goodbye, and delete it!

2:exit
Almost Done!
Now, repeat the first process, only replace zd1211-firmware with the name of the new folder of the firmware

Your welcome
-PCessna

---

### Post by AdaMich on 2009-01-24
PCessna- your post was a great help to me. But I am still stuck. 
I have the xd1211-firmware folder in the correct place, but it does not seem to make unbuntu recognize the wireless. I have ubuntu 8.10 and a hawking HWU54G USB stick. When I go to the network symbol it just lists the wired ethernet, with no indication that there is wireless at all.

What would prevent it from just working? I have struggled for 3 days with this.:( Any help would be appreciated.

---

### Post by PCessna on 2009-03-01
> **AdaMich said:**
> PCessna- your post was a great help to me. But I am still stuck. 
I have the xd1211-firmware folder in the correct place, but it does not seem to make unbuntu recognize the wireless. I have ubuntu 8.10 and a hawking HWU54G USB stick. When I go to the network symbol it just lists the wired ethernet, with no indication that there is wireless at all.

What would prevent it from just working? I have struggled for 3 days with this.:( Any help would be appreciated.
Try reversing drivers changes, Then halt your computer. Bootup with it in, or put the stick in with no drivers and reboot, thisway, the kernal sees it unknown first. Then install drivers, and reboot with making sure the stick USB is still in

-PCessna

---

