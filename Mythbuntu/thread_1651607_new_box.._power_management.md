---
title: "new box.. power management"
date: 2010-12-23
forum: Mythbuntu
---

### Post by oldsoundguy on 2010-12-23
same project, another question.
I made the mistake of buying a WD Green drive and now want to know how to keep it from parking as I run background stuff for BOINC when computer space and time is available.
Cannot find the power management utility that comes in Ubuntu in Mythbuntu .. (really beginning to dislike the limitations of menus in Myth and may consider blowing it out and putting Ubuntu WITH Myth on the box instead of the Mythbuntu.)

Box now running 10.04 with MythTV installed.  Gives me a bunch more flexibility and control of the box itself.  (and the ability to print screen on my network.) Will see how Myth works in that setup

---

### Post by 4dognight on 2010-12-24
The desktop in Mythbuntu is stripped down to keep it lightweight. I just add any other programs to my mythbunutu desktop as needed. If you want a full desktop you are better of going with Ubuntu and then installing Mythtv. But you will use more resources if that is a concern.

---

### Post by oldsoundguy on 2010-12-24
> **4dognight said:**
> The desktop in Mythbuntu is stripped down to keep it lightweight. I just add any other programs to my mythbunutu desktop as needed. If you want a full desktop you are better of going with Ubuntu and then installing Mythtv. But you will use more resources if that is a concern.

resource usage is really not a concern .. 3.2 hyperthreaded processor, 3gb of ram, nividia card with 1gb of ram and a 1tb  drive.

The point is that UTILITIES ... the things we need to set up the box and to control it, should be part of the Mythbuntu install .. and they are not.  A newb to Ubuntu or any Linux is NOT going to "open terminal" and enter code.

---

### Post by newlinux on 2010-12-24
If you wanted to install the standard ubuntu desktop onto your mythbuntu install you could have done:

```
 sudo apt-get install ubuntu-desktop
```

Or do it through mythtbuntu-control-centre. That will give you the standard ubuntu gnome desktop.

---

### Post by ian dobson on 2010-12-24
Hi,

Can't your use hdparm from the terminal as root to set the powerdown time for harddisks:-

 hdparm --help

```

hdparm - get/set hard disk parameters - version v9.27, by Mark Lord.

Usage:  hdparm  [options] [device] ..

Options:
 -a   Get/set fs readahead
 -A   Get/set the drive look-ahead flag (0/1)
 -b   Get/set bus state (0 == off, 1 == on, 2 == tristate)
 -B   Set Advanced Power Management setting (1-255)
 -c   Get/set IDE 32-bit IO setting
 -C   Check drive power mode status
 -d   Get/set using_dma flag
 -D   Enable/disable drive defect management
 -E   Set cd/dvd drive speed
 -f   Flush buffer cache for device on exit
 -F   Flush drive write cache
 -g   Display drive geometry
 -h   Display terse usage information
 -H   Read temperature from drive (Hitachi only)
 -i   Display drive identification
 -I   Detailed/current information directly from drive
 -k   Get/set keep_settings_over_reset flag (0/1)
 -K   Set drive keep_features_over_reset flag (0/1)
 -L   Set drive doorlock (0/1) (removable harddisks only)
 -M   Get/set acoustic management (0-254, 128: quiet, 254: fast)
 -m   Get/set multiple sector count
 -N   Get/set max visible number of sectors (HPA) (VERY DANGEROUS)
 -n   Get/set ignore-write-errors flag (0/1)
 -p   Set PIO mode on IDE interface chipset (0,1,2,3,4,...)
 -P   Set drive prefetch count
 -q   Change next setting quietly
 -Q   Get/set DMA queue_depth (if supported)
 -r   Get/set device  readonly flag (DANGEROUS to set)
 -R   Obsolete
 -s   Set power-up in standby flag (0/1) (DANGEROUS)
** -S   Set standby (spindown) timeout**

```

Regards
Ian Dobson

---

### Post by thatguruguy on 2010-12-24
> **oldsoundguy said:**
> resource usage is really not a concern .. 3.2 hyperthreaded processor, 3gb of ram, nividia card with 1gb of ram and a 1tb  drive.

The point is that UTILITIES ... the things we need to set up the box and to control it, should be part of the Mythbuntu install .. and they are not.  A newb to Ubuntu or any Linux is NOT going to "open terminal" and enter code.

A n00b can always install the ubuntu desktop if he needs to. Most people don't need to worry about setting up power management. Those who need it can install it.

Likewise, most people aren't running printers off their mythbuntu boxes. Instead, they are using their mythbuntu boxes as p.v.r.s, as intended.

You can always just set up a normal ubuntu install, and then install the mythtv package if that's what you want.

EDIT: And I refuse to believe that a n00b to ubuntu or any linux is going to refuse to open a terminal, unless he or she is mentally defective in some significant way.

---

### Post by LowSky on 2010-12-24
The green drives are meant to be energy saving. They accomplish that by spinning down. If you give them things to do they will not spin down, but with the Green drive their own firmware is also going to limit the full control you might be looking for. Dont forget Green drives operate slower too They dont run at 7200RPM like most newer drives. So they seem slower even with spin down turned off.

---

