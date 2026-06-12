---
title: "Beta2 64bit live cd reboots upon loading desktop"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lavinog on 2011-04-19
I downloaded the beta2 iso and burned to a DVD:
```
$ md5sum ubuntu-11.04-beta2-desktop-amd64.iso 
fd98ed30077cf68620b78e19db053917  ubuntu-11.04-beta2-desktop-amd64.iso

```

The DVD will boot, and has passed the disk check.  When the live environment loads, it will eventually show the desktop wallpaper (nothing else) then the system will reboot instantly.

I have tried with nomodeset, and it does the same, however there was a kernel message about TSO and mmio address already in use (I will try and get the exact message soon.) Shortly after that, there is a message in red that says anacron is shutting down...the wallpaper shows, then the system reboots.

I am using an AMD system with an ATI Radeon 3650.
I will file a bug on this after I try a couple of other things, and find out what package to file it under.  I am suspecting that this will likely be a kernel or xorg bug.

Later in the afternoon, I will try using a USB stick and also try on a similar machine.

Has anyone else experienced this, or have any ideas on how to diagnose this issue?

---

### Post by lavinog on 2011-04-19
The error I got with nomodeset:
```

[27.029426] SP5100 TCO timer: mmio address 0xfec000f0 already in use

```


I was able to boot with the all F6 options set (nomodeset, noapci...all except the free software only option)
It took a really long time to get to the desktop but when I did, I found this in dmesg:
```

[   26.147242] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   26.236280] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   26.251813] SP5100 TCO timer: Watchdog reboot not detected.
[   26.254159] SP5100 TCO timer: initialized (0xffffc900010680f0). heartbeat=60 sec (nowayout=0)

```

Searching the mmio in use error gave me this bug:
[Natty: the driver sp5100_tco prevents PC startup](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740011)

---

### Post by lavinog on 2011-04-25
The beta2 disk works on a similar machine.  The difference is the machine is using the onboard video card (ati radeon hd3200) while the machine that it doesn't work on has a dedicated card (ati radeon hd3650)

I will try and remove the dedicated card later and see if it does address the issue.

---

