---
title: "Booting From a USB Drive"
date: 2010-05-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mrpinchy on 2010-05-24
Hey All,

I want to try Maverick, but am not willing to give up one of my installs to it.

I would like to know if I can take a 8gig thumb drive I have, wipe it, format it, install Maverick on it, and boot it like it was another hard drive?

The other option is to buy another hard drive and swap them out...      ...or go without.

I'm having fun & great success using Ubuntu, for a noob.  I don't know a thing, except that I'd like to try to help with testing.

Thanks,
Joe.

---

### Post by ronacc on 2010-05-24
as long as your mobo bios can be set to boot from a usb stick it works fine I use it instead of a cd for installing dailies .

---

### Post by kansasnoob on 2010-05-24
When installing to an external drive you must be careful where you install grub! By default it will be installed to the internal drive and you don't want that.

You must first see what designation Ubuntu gives to the external. You should be able to do that by running:

```
sudo fdisk -l
``` 

With the external plugged in. Since it lists the size of the drives it should be easy to identify the external.

This would also be an excellent time to describe drive and partition designations in Ubuntu:

Drives are designated as /dev/sda, /dev/sdb, /dev/sdc, etc. the last letter indicates the drive number, eg:
/dev/sda = drive #1
/dev/sdb = drive #2
/dev/sdc = drive #3

Partititions are designated with a number following the drive designations, eg:
/dev/sda1 = drive #1/partition #1
/dev/sda2 = drive #1/partition #2
/dev/sdb1 = drive #2/partition #1

It is almost never a good idea to install grub to a partition!

Once you know the proper designation you can go ahead with the install, but when you get to the last screen you'll see an Advanced button in the lower right hand corner:

[http://members.iinet.net.au/%7Eherman546/p22/035.png](http://members.iinet.net.au/%7Eherman546/p22/035.png)

Click on it and you'll see that you can "toggle" through a list of devices:

[http://members.iinet.net.au/%7Eherman546/p22/036.png](http://members.iinet.net.au/%7Eherman546/p22/036.png)

Be sure to select the proper device!

Credit here for the screenshots:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by garvinrick4 on 2010-05-24
I have experimented with quite a few giving them /boot  a / and a small swap and as long
as the in advanced I used sba, sbc, sbd, ect. ect. ect. and never the partition # as stated before me. Putting the boot in sba would allow it to go into my little 200 meg sba1 /boot
and be found in my sda2 or whatever # my / partition is for replacing grub from Live CD if needed. 
 It would place itself in my sda mbr when plugged in. When not plugged in would not be in
sda's mbr so it was fine. Do not use on friends computer with Windows only will overwrite Windows boot manager if done with partitions instead of UBS creator or netbootin or like.
 Some USB 's just flat will not work to boot off of. No rhyme nor reason just will not be bootable. The one that always works for me is Centon for some reason. Some work with 
USB creator some work with unetbootin and some work with /boot and a /, and some do not work as bootable at all.????
 You cannot go wrong with kansasnoobs assistance but I thought I would throw in my experience with the USB flash drives.

---

### Post by bennachie on 2010-05-24
There are (at least) two possible ways you might want to use a system properly installed on a USB stick or an external USB hard drive (as opposed to creating the equivalent of a LiveCD on such a device). 

The first, and simpler, option is to use the USB device for test purposes, leaving the partitioning scheme on the main hard drive (sda) undisturbed. In that case, you can opt to have the grub located on sda but to install the test system on the USB device (sdb or whatever). The Ubuntu installer makes this easy, and you can use the swap space on your hard drive while you are at it, and set up only a single "/" partition on the USB device. So long as the USB device is plugged in when you fire up your computer, you'll be able to select it from the boot options in the normal manner. This may be quite a good approach in your particular circumstances.

The second option, and the one on which earlier contributors have focused, is to have a completely free-standing system on the USB device, and to use the BIOS to establish the boot priority. For some reason, making this work requires a bit more tip-toeing round the tulips when installing Ubuntu that when using the graphical installers in Fedora or Mandriva. That's reflected in the advice you have received. Perhaps the issue could be addressed in Maverick - I can't see that there need be a Grub1 versus Grub2 problem here.

Obviously, the second option results in a more flexible setup (the USB stick will work on almost any computer, unless you've selected a special graphic driver or something of that kind) but, if you want to use and/or test suspend/hibernate, you'll need to set aside a swap space on the USB device.

---

### Post by andrewabc on 2010-05-24
I would not 'install' to usb. I did that before and it became grub disaster.

system->admin->usb creator
is best option.
Although this might not be possible until .iso are released.
Not sure when they start doing dailies. Alpha 1 will be released June 3, so wait until then if needed.

---

### Post by ranch hand on 2010-05-25
I run on an dual drive external enclosure and have no trouble with it at all.  I can boot to it from the internal (I usually don't have them on when running the testing OS' that are on the external) and I can boot to the internals from there if I want.

---

### Post by LiquidMeson on 2010-05-25
> **mrpinchy said:**
> Hey All,
I would like to know if I can take a 8gig thumb drive I have, wipe it, format it, install Maverick on it, and boot it like it was another hard drive?
Joe.

(assume windows)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) install, run, play. :roll:

---

### Post by cariboo on 2010-05-25
Unetbootin is in the repositories, no need to download it from Sourceforge.

---

### Post by dhalbert on 2010-06-06
I was unable to get Maverick Alpha 1 netbook to boot from two different USB sticks prepared with unetbootin-471 on Windows.

However, using usb-creator (System->Administration->Startup Disk Creator) worked fine.

The unetbootin attempts failed with errors about "inserting ramzswap" and "inserting vesafb". Unfortunately the errors go by too fast to catch all the details.

---

