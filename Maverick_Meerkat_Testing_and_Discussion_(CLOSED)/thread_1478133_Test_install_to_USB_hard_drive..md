---
title: "Test install to USB hard drive."
date: 2010-05-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by gibbylinks on 2010-05-09
Hi,

I'm looking forward to helping out with testing.

What I'd like to do is utilise a 40gb USB drive that I have spare to install Meerkat on use it for testing, leaving my Lucid install intact on my local hard drive.

I installed Lucid on to the drive, with a view to applying the upgrades to Meerkat, but it screwed up grub and I had to reinstall GRUB on the local drive. Now I can't get to boot onto the USB.

Does anyone else use a similar setup, could they point me to any tutorials. I'd like to be able to remove the hard drive and just use the laptop normally, or plug it in boot Meerkat up and have a play without worrying about borking it.

Would love to be able to test ISO's later on.

I appreciate that to some I probably come across as a noob who should steer clear, but hey we all gotta start somewhere and I have been computing since Speccie days... :P and running Linux now for several years.

Cheers

---

### Post by buellman on 2010-05-09
I think you just have to specify where grub should be installed... you most likely want to install grub in the MBR of your external HDD.
But it is just a guess.

Greets. Buellman

---

### Post by cariboo on 2010-05-09
@buellman is correct, put grub on the mbr of the external drive, that way you can boot into your regular install if you disconnect the drive.

Make sure that you have the bios set to boot from the external drive before the internal drive.

---

### Post by gibbylinks on 2010-05-09
Now you've confused me slightly, put GRUB on external drive. Surely then if it's unplugged I can't boot ?

Or do you mean install it on there as well ? :P

My BIOS doesn't have a boot order. It has a boot menu where you can select the boot device.

---

### Post by buellman on 2010-05-09
I think you should install it there as well. Don't touch the MBR of your internal HDD to not mess with your productive system.

Now... in order to boot from the external hdd (where your testing system is installed) you have to specify in your BIOS that it should try to boot from an USB-device BEFORE trying to boot from your internal hdd.
It should be orderd like that:
- Floppy (if you have one and would like to boot from that... else: forget Floppy)
- CD-Rom
- USB-Device
- Internal HDD

So if in question your system will try to boot from Floppy. If there is nothing to boot from it will try the CD-Rom. If there ist nothing it will try to boot from your USB-device (hopefully there is an MBR with grub in it). If there is nothing it will try to boot from your internal HDD (where should be another MBR with another grub).

Hope that helps :-) If not: ask again. 

Greets. Buellman

---

### Post by ranch hand on 2010-05-09
When you install grub you can choose what MBR  it goes on.  Every drive has one.

If you install 10.10s grub on the external it will boot there.  If 10.04s grub is installed on the internal it will boot when you boot from there.

10.04s grub should be able to boot both drives with that setup but you will probably not be abel to boot 10.04 from the external with grub working from that MBR.

Can you turn off or disable your internal HDD in Bios?  My test platform is a dual external enclosure and  I run it with my internal drives turned off so that there is no chance of screwing something.  I will sometimes turn the external on while on the internals to chroot, partition or transfer files to the test  OS'.

I am on the external right now.

---

### Post by xebian on 2010-05-09
I'm guessing the USB drive is not known yet during grub time.

---

### Post by cariboo on 2010-05-09
If you have a fairly recent system, the usb drive should be detected by the bios if it is plugged in and turned on. I use MSI motherboards, they allow you to sent boot order as well as disk order. Which helps when you have 6 hard drives connected to a motherboard.

---

### Post by ubername on 2010-05-10
I have a USB drive with a Lucid and a Maverick on, and an HDD with a Karmic, 2 Lucids, Vista and Win7. I have grub on the MBR of both drives. If I boot with the USB drive switched on I can boot into all of the above, as grub sees all the drives/ partitions. If I boot with the USB drive switched off (which I hardly ever do) I can get into the OS's on the HDD. 

A few caveats: 
Only one install controls the USB grub at any one time, so if I am playing in other than the main install and want to update-grub I need to

```
grub-mkconfig -o path-to-main-install/boot/grub/grub.cfg
```

If I want to boot from another USB device (e.g. USB flash drive) I need to switch off the USB HDD


Apart from this the set-up works well, and I have not had any problems with it.

---

