---
title: "Can't Play DVDs"
date: 2011-05-17
forum: Multimedia Software
---

### Post by root45 on 2011-05-17
I know this is a popular topic that often has an easy fix, but I've read about 20 other threads that all say the same thing.

These are the things I've already done

```
sudo apt-get install ubuntu-restricted-extras

sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh

sudo apt-get install libdvdcss2

sudo apt-get install w64codecs
```

and probably some other codecs and whatnot that I can't remember at the moment.

I've tried three different DVDs on both VLC and MoviePlayer. VLC gives the error "VLC cannot set the DVD's title. It possible cannot decrypt the entire disc" and then plays the FBI warning before exiting with more errors like that. MoviePlayer just plays the warning and exits without error (kind of annoying).

I'm running Ubuntu 64-bit desktop 11.04. Thanks for any help.

---

### Post by root45 on 2011-05-20
So originally I thought this was a hardware issue because I kept getting a bunch of errors related to I/O and my DVD drive. But I just bought a new DVD drive and I'm having the same problem. I switched out the SATA cables and tried a couple different SATA ports on my mother board, so I'm pretty sure that's not the issue.

Basically, the situation is this. I start up and after BIOS loads, but before GRUB shows up, I get a quick error saying "error: cdrom read error". Then I boot normally, and everything is seemingly great. If I put in a DVD, it mounts, but I'm not able to play it or copy the files off of it.

I did a dmesg | tail before and after putting in the DVD.

Before

```

[  119.467771] wlan0: direct probe responded
[  119.515673] wlan0: authenticate with 00:23:69:5b:30:0f (try 1)
[  119.519117] wlan0: authenticated
[  119.520288] wlan0: associate with 00:23:69:5b:30:0f (try 1)
[  119.522256] wlan0: RX AssocResp from 00:23:69:5b:30:0f (capab=0x411 status=0 aid=2)
[  119.522259] wlan0: associated
[  119.523002] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  119.840039] Intel AES-NI instructions are not detected.
[  119.976906] padlock_aes: VIA PadLock not detected.
[  129.770718] wlan0: no IPv6 routers present

```

After

```

[  256.096324] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  256.096326] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  256.096329] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  257.539308] wlan0: authenticate with 00:23:69:5b:30:0f (try 1)
[  257.541105] wlan0: authenticated
[  257.541129] wlan0: associate with 00:23:69:5b:30:0f (try 1)
[  257.543374] wlan0: RX AssocResp from 00:23:69:5b:30:0f (capab=0x411 status=0 aid=1)
[  257.543378] wlan0: associated
[  273.100632] UDF-fs: Partition marked readonly; forcing readonly mount
[  273.126058] UDF-fs INFO UDF: Mounting volume 'DVD_MOVIE', timestamp 2002/04/15 14:14 (1ed4)

```

so no errors there. With my old drive I was getting a whole host of errors, none of which seem to be appearing now. Unfortunately they don't seem to be the cause of the problem.

Does anyone have any idea what's wrong or how I might diagnose this?

---

### Post by SeijiSensei on 2011-05-20
Try **mplayer**.  Use "mplayer dvd://1" at the command prompt to play the first chapter on the disk (which might be the FBI warning).  Replace "1" with "2", etc., to see if you can play the other chapters.

If there are problems, mplayer will report them to you in the terminal window.

---

### Post by root45 on 2011-05-20
That particular command returns

```

MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /dev/dvd
No such file or directory
Couldn't open DVD device: /dev/dvd (No such file or directory)
No stream found to handle url dvd://1


Exiting... (End of file)

```

I think part of the issue may be that there is no /dev/dvd on my system. There's a /dev/dvd1, and if I do

```

mount /dev/dvd1 /media/dvdtest

```

it mounts the DVD there. However, running

```

mplayer dvd1://1

```

returns

```

MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd1://1.
No stream found to handle url dvd1://1


Exiting... (End of file)

```

---

### Post by root45 on 2011-05-20
Just an update to the issue. I've just tried playing a DVD on the same computer running Windows 7 and there was no issue. So now I'm just confused. I assumed the error message at boot indicated a hardware issue, but Windows doesn't seem to care. So I guess it's just Ubuntu that has an issue.

---

### Post by mc4man on 2011-05-20
First of all - the mplayer command was wrong. Mplayer defaults to /dev/dvd, to use a different /dev link you need to specify. You also need to know what title you want - title 1 does not always have the main title or anything playable

As Ex. - on /dev/dvd1 I want to play title 2
```
mplayer -dvd-device /dev/dvd1  dvd://2
```

Any way I'd put mplayer aside for the moment
Why don't you run this and post what's in the *-cdrom: section(s)
```
sudo lshw -C disk
```

---

### Post by root45 on 2011-05-20
Okay, so I'm not entirely sure what happened, but now it seems to be working. The only thing I did was boot into Windows and play a DVD there. I don't see why that would affect this at all though.

I'm still getting "error: cdrom read error" at boot (after BIOS, but before GRUB), and I'd like to fix that. But I guess I can live with it as long as everything else works.

The output under cdrom of

sudo lshw -C disk

is

```

*-cdrom
       description: DVD-RAM writer
       product: iHAS124   B
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/THE_NEVERENDING_STORY_II
       version: AL0L
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted status=ready

```

---

### Post by mc4man on 2011-05-20
> The only thing I did was boot into Windows and play a DVD there
Most likely windows set a region on the drive, because it uses a licensed player the region has to be set. (only has to be done once

While in linux you don't always need the region set on a drive if not set it can prevent the player from acquiring the decryption keys.

As far as the pre grub cdrom message - probably nothing to worry about - do you have it set in bios to boot from the cdrom drive before the hdd?

If you wish in vlc you can set the default device to your drive,  see screen, use either /dev/dvd1 or /dev/sr0 (I use the latter

To set vlc - Tools > Preferences > Input & Codecs

The /dev links for that drive can be set to what is still the defaults of some apps if you wish, only takes a min or so, (/dev/dvd, /dev/cdrom, dev/dvdrw, /dev/cdrw

The drive will always be /dev/sr0  which is all you really need to remember

If you want to reset your dev links then run this in a terminal, copy and paste to post, I'll show you how to adjust

```
gedit /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by root45 on 2011-05-20
Awesome. I've changed the defaults where needed. Thanks for the help.

The CD drive was set to boot first in the BIOS, but even after changing it I still get the error.

---

