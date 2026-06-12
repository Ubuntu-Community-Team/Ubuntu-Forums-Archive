---
title: "Make USB webcam always /dev/video2 ?"
date: 2012-06-13
forum: Multimedia Software
---

### Post by fixitdude on 2012-06-13
Is there a "Ubuntu friendly" way I can make a USB webcam always come up as /dev/video2 ?

Every time I re-boot I have to unplug the USB cam to get it to show up as the last video device. It comes up randomly otherwise.

Something that survives a Ubuntu system / LTS version upgrade?

I found this procedure, but I don't think it will survive a LTS version upgrade.

I know in a year I will forget about it and may upgrade over it.

```

Figure out the attributes that identify the device uniquely (usually, vendor and product IDs and/or serial numbers work):

udevadm info -a -p /sys/class/video4linux/video0

Then write rules that create the symlinks, e.g.:

cat > /etc/udev/rules.d/83-duplicate_devs.rules << "EOF"
# Persistent symlinks for webcam and tuner
KERNEL=="video*", ATTRS{idProduct}=="1910", ATTRS{idVendor}=="0d81", \
    SYMLINK+="webcam"
KERNEL=="video*", ATTRS{device}=="0x036f", ATTRS{vendor}=="0x109e", \
    SYMLINK+="tvtuner"
EOF

The result is that /dev/video0 and /dev/video1 devices still refer randomly to the tuner and the web camera (and thus should never be used directly), but there are symlinks /dev/tvtuner and /dev/webcam that always point to the correct device. 


```

---

### Post by Cheesehead on 2012-06-14
Creating a udev rule (which is what you did) really is the best way to specify a device rule. That's exactly what udev is for.

If you want to save customizations across upgrades and even some reinstalls, create a folder for tracking all your customizations (like  [FONT="Courier New"]/home/me/system-customizations[/FONT]).

Put a hard link to the rule in the folder. Hard links are good for this instead of copies (prevents version confusion).

Put a bunch of #comments in the rule to remind you what it's for, when you did it, the path it should be installed to, the URL of the original instructions, and any other related files that a change would require further edits to.

Simply documenting ALL your changes, and keeping an organized record in one place like this, can be a huge timesaver six months later.

---

