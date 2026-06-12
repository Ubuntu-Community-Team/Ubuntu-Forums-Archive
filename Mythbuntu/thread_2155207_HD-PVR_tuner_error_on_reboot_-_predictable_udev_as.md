---
title: "HD-PVR tuner error on reboot - predictable udev assignment for HD-PVR &amp; PVR-500"
date: 2013-06-17
forum: Mythbuntu
---

### Post by one30nav on 2013-06-17
I'm sure this is a common issue, but I had to dig a little to get an answer for my setup - Ubuntu 12.04 64-bit & Mythtv 0.26 with a HD-PVR & PVR-500. 

ISSUE: Had an error with my HD-PVR & PVR-500 on reboot -- the HD-PVR would jump from /dev/video2 to /dev/video1 and conflict with the PVR-500. Error showed up in "information" as two out of the three tuners erroring out and correctable only by hard reboot or by deleting all capture cards and re-installing.

ANSWER: Of course, to forcibly assign devices under udev.

Great initial guidance from here: [http://linhes.org/projects/linhes/wiki/Predictable_video_assignment_for_HD-PVR_using_udev](http://linhes.org/projects/linhes/wiki/Predictable_video_assignment_for_HD-PVR_using_udev)

Here's what I did to get mine working from linhes (above link) and numerous sources:

```
udevadm info -a -p $(udevadm info -q path -n /dev/video2)
```

Look for ATTRS{serial}=="xxxxxxxx" for Hauppauge HD PVR.

```
udevadm info -a -p $(udevadm info -q path -n /dev/video0)
```

Look for ATTRS{subsystem_device}=="xxxxxx"

```
udevadm info -a -p $(udevadm info -q path -n /dev/video1)
```

Look for ATTRS{subsystem_device}=="xxxxxx"

```
cd /etc/udev/rules.d

sudo nano 78-hdpvr.rules
```

My resulting 78-hdpvr.rules file looks like this. So, cut & paste for a head start then tweak yours:

```
KERNEL=="video*" , ATTRS{product}=="Hauppauge HD PVR" , ATTRS{serial}=="00A76924" , SYMLINK ="hdpvr"
KERNEL=="video*" , SUBSYSTEM=="video4linux" , ATTRS{vendor}=="0x4444" , ATTRS{device}=="0x0016" , ATTRS{subsystem_vendor}=="0x0070" , ATTRS{subsystem_device}=="0xe807" , ATTR{index}=="0" , SYMLINK ="pvr500-1"
KERNEL=="video*" , SUBSYSTEM=="video4linux" , ATTRS{vendor}=="0x4444" , ATTRS{device}=="0x0016" , ATTRS{subsystem_vendor}=="0x0070" , ATTRS{subsystem_device}=="0xe817" , ATTR{index}=="0" , SYMLINK ="pvr500-2"
```

Reboot

Run mythtv-setup; add a capture card; manually type in "/dev/hdpvr" or "/dev/pvr500-1" or "/dev/pvr500-2" (these options do not show up if trying to scroll past /dev/video0, etc. So, manually input)

Now things are rock-solid after reboots. Hope this helps.

---

