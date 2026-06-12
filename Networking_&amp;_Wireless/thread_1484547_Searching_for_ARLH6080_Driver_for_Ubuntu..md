---
title: "Searching for ARLH6080 Driver for Ubuntu."
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Mimichii on 2010-05-15
So I figured out how to connect wireless to the internet through my Ubuntu O/S, but evidently I need the driver to pick up any wireless networks around.

Anyway I own an Airlink101 AWLH6080 card for my desktop.  I found this video which told me exactly what I need to do. [http://www.youtube.com/watch?v=hH-4u9x0e-Y&playnext_from=TL&videos=0Kz1dNSC9VQ](http://www.youtube.com/watch?v=hH-4u9x0e-Y&playnext_from=TL&videos=0Kz1dNSC9VQ)

Anyway, does anyone know where I can get that driver from?  The one on the Airlink website itself doesn't do anything for Ubuntu, and I checked out Ralink, but I don't know what to do from there.

Any help is appreciated, thank you!

---

### Post by BoneKracker on 2010-05-15
I haven't looked at your video.

If there's no linux driver available for the device, ndiswrapper is what you've got to use.  First check if there's a linux driver available. Keep in mind that the linux drivers for such devices are often produced by the manufacturers of the chipset as opposed to the device itself.  So you should investigate what chipset your device is based on and look for drivers for that.  The linux kernel may already include the driver, and you may be able to simply load the module.

If not, the chipset vendor may have a kernel module and firmware (driver) available.  This may or may not be in the ubuntu repository.  The vendor may have source code you can download from their website and compile to produce a module.  Although, if you are new to linux, it's probably easier for you to just use the Windows driver.

As you probably know, ndiswrapper uses the Windows driver.  You can usually scarf it from the software installation download provided from the vendor, or from the software installation CD.  You need to know what the file(files) is(are) named, and you may need to decompress the installer if it came in archived form.

If you've already been using the device on a Windows machine, the file(s) you need may already be decompressed on that machine.  Windows installers have a habit of leaving installation files lying around in places like the root directory (C:\vendor, for example) and other places.

You can probably find a generic ndiswrapper HOWTO somewhere on the internet with guidance about how to grab the necessary windows driver files.

---

### Post by chili555 on 2010-05-15
This is evidently a Ralink RT2860 device. There is a driver already in the kernel. Please open a terminal and do:```
sudo modprobe rt2860sta
iwconfig
```Did a wireless interface get created? Can you click the Network Manager icon and connect?

---

### Post by Mimichii on 2010-05-16
@BoneKracker-- Yeah I've actually been trying to use ndiswrapper to attempt to use windows drivers for my card; however, none of them work.. So I was trying to see what else may be available.

Also my computer was recently wiped, so I'm missing quite a few files.
 
@Chili-- I tried that, but it says: All config files need .conf: /etc/modprobe.d/ndiswrapper.
And I wasn't able to establish a wireless connection due to not being able to find the proper wireless file needed yet.

---

### Post by BoneKracker on 2010-05-16
@Mimichii: Lets see what ralink drivers are in the kernel the Ubuntu developers gave you.  What is the output of this command:```
find /lib/modules/$(uname -r)/ -type f -iname '*.o' -or -iname '*.ko' |grep rt[23]
```

@chili555: I have a USB NIC based on the Ralink 2870 chipset.  It was working fine in 2.6.32 and then broke with 2.6.33.  From what I've read, I must wait for a new driver from Ralink.  I wonder if that's the same problem with the Ralink 2860 chipset.

@Mimichii: FYI, here's some more background for you, since I happen to also be a Ralink user.  Ralink drivers are obviously in flux right now, and emerging.  Also, there seem to be two alternative families of drivers:

I think the drivers in the "staging" section of the kernel (rt2860sta/rt3060sta and rt2870sta/rt3070sta) were developed by Ralink or based directly on the Ralink GPL code (which you can get at their website).  rt2870sta is what I was using for my 2870-based USB NIC, but when I last tried in under 2.6.33 it didn't work any more.  I didn't try hard because I don't need it right now and haven't tried lately.

It is interesting to know there is also another family of Ralink drivers in the kernel (not in staging but in the main drivers/network_devices section, although marked "experimental").  These I think are built on the Ralink "2x00" library developed by the Serialmonkey project.  I haven't tried one from that family, and it's not likely ubuntu enabled it in your kernel.  The appropriate one of those for a 2860 would apparently be "rt2800pci" but in the kernel it's marked "very experimental" and the description says:
> This adds support for rt2800 wireless chipset family.  Supported chips: RT2760, RT2790, RT2860, RT2880, RT2890, RT3052.  This driver is non-functional at the moment and is intended for developers.

So, bottom line, I might try rt2860sta if I was familiar with how to set up wireless in linux.  If not (or if it didn't work), I'd probably set up ndiswrapper if I needed the device to work now.  Then, I'd keep tabs on updates to the rt2860sta driver.

---

### Post by chili555 on 2010-05-16
> I wasn't able to establish a wireless connection due to not being able to find the proper wireless file needed yet.Huh?

I thought that rt2870sta was the file you needed. You don't need *both* the native rt2870sta and the Windows .inf and .sys files; you need one or the other. Let's see what is happening under the hood. Please post:```
dmesg | grep rt2
lsmod | grep rt2
iwconfig
```Thanks.

---

### Post by BoneKracker on 2010-05-16
rt2860sta (from what you said earlier)

sorry if I caused confusion

---

