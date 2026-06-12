---
title: "Mythbuntu 12.04.2 64-bit ISO image too big for a CD-R!"
date: 2013-03-11
forum: Mythbuntu
---

### Post by neutron68 on 2013-03-11
I downloaded the 12.04.2 64-bit ISO image last night.  
When I tried to burn it onto a 700MB CD-R, the CD-R software warned that the disc image was bigger than the 700MB disc size!

How are people burning this CD image onto a CD-R?

Eric

---

### Post by AlecJ on 2013-03-11
Yes at 770.7 Gb its too big, I used a USB stick last time or you could use DVD-R
So I guess the answer is there not.

---

### Post by ibjsb4 on 2013-03-11
Another option would be the mini iso.

---

### Post by neutron68 on 2013-03-11
> **ibjsb4 said:**
> Another option would be the mini iso.
There is NO mini ISO option at [http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads).

---

### Post by ibjsb4 on 2013-03-11
Thats because one mini iso covers all the flavors :)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

And install mythbuntu-desktop to it.

---

### Post by neutron68 on 2013-03-11
> **ibjsb4 said:**
> Thats because one mini iso covers all the flavors :)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
There is no mention of Mythbuntu anywhere on that page, and no mention that it will allow you to install anything but stock Ubuntu.

Eric

---

### Post by ibjsb4 on 2013-03-11
There are two ways to do it.

#1  Use the built in UI installer and select the mythbuntu-desktop during the install.

#2 Select option #2 and do a terminal only install.  After that is completed:

```
sudo apt-get install mythbuntu-desktop
```

Any desktop that is installed (ubuntu, xubuntu, myth ..) with the mini iso will be downloaded, it is not part of the mini CD.  The mini iso CD is only 27MB.  Any desktop can therefore be installed using the mini iso.

There seem to be many other myth packages offered, so I can't tell you if you need to install anything else.  The myth-desktop is a 600+MB download, so that should be a good start :)

[ATTACH=CONFIG]240060[/ATTACH]

---

### Post by neutron68 on 2013-03-12
An install over the Net takes 1-3 hours.  An install off a CD-R takes less than an hour.  That's the bottom line.

For me, the whole point of installing from a 650-700MB CD is that I am not held hostage, sitting at the computer, waiting for files to download, and being asked a question every 10 minutes for the duration of the install.

I'd prefer to see the 12.04.2 ISO fixed so it fits on a CD-R.
Can someone work on that, please?

Eric

---

### Post by ibjsb4 on 2013-03-12
sudo apt-get [COLOR=#ff0000]-y[/COLOR][COLOR=#000000] install mythbuntu-desktop[/COLOR]

---

### Post by tgm4883 on 2013-03-12
> **neutron68 said:**
> An install over the Net takes 1-3 hours.  An install off a CD-R takes less than an hour.  That's the bottom line.

For me, the whole point of installing from a 650-700MB CD is that I am not held hostage, sitting at the computer, waiting for files to download, and being asked a question every 10 minutes for the duration of the install.

I'd prefer to see the 12.04.2 ISO fixed so it fits on a CD-R.
Can someone work on that, please?

Eric

Install from a USB drive. I don't think there is any hardware available that we would recommend Mythbuntu running on that can't boot from USB. If there is, burn it to a DVD.

If you can find 70MB worth of stuff on the ISO that can be removed, please let me know.

---

### Post by tgm4883 on 2013-03-12
Wouldn't that fail though if questions are asked that aren't Y/N (eg. Mysql installs request you to make a password I think). If so, then he could at least

```
sudo apt-get -d install mythbuntu-desktop
```

Come back later then

```
sudo apt-get install mythbuntu-desktop
```

---

### Post by neutron68 on 2013-03-12
> **tgm4883 said:**
> Install from a USB drive. I don't think there is any hardware available that we would recommend Mythbuntu running on that can't boot from USB. If there is, burn it to a DVD.

If you can find 70MB worth of stuff on the ISO that can be removed, please let me know.
I can definitely burn a DVD-R from the ISO, if that's what it takes. 

PLEASE...If the 12.04.02 64-bit ISO file only fits on a DVD-R, can it be noted out on the download page, to prevent confusion?
[http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads)

By the way, I tried 2 different ISO to USB programs and both produced a FAILED bootable USB Flash Drive.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Neither program produced a USB Flash drive that successfully booted into the Mythbuntu installer.  

Both gave errors about invalid or corrupt img file (or similar).  I can take screen photos, if you don't believe.

Yes, I checked the MD5SUMS code to be sure the ISO was not corrupt.
1065b482382203d367cf7ce1c69b7c51  (for mythbuntu-12.04.2-desktop-amd64.iso)

Based on my experience, the 12.04.02 64-bit ISO file is NOT compatible with bootable USB Flash drives.

Eric

---

### Post by tgm4883 on 2013-03-13
> **neutron68 said:**
> I can definitely burn a DVD-R from the ISO, if that's what it takes. 

PLEASE...If the 12.04.02 64-bit ISO file only fits on a DVD-R, can it be noted out on the download page, to prevent confusion?
[http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads)

By the way, I tried 2 different ISO to USB programs and both produced a FAILED bootable USB Flash Drive.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Neither program produced a USB Flash drive that successfully booted into the Mythbuntu installer.  

Both gave errors about invalid or corrupt img file (or similar).  I can take screen photos, if you don't believe.

Yes, I checked the MD5SUMS code to be sure the ISO was not corrupt.
1065b482382203d367cf7ce1c69b7c51  (for mythbuntu-12.04.2-desktop-amd64.iso)

Based on my experience, the 12.04.02 64-bit ISO file is NOT compatible with bootable USB Flash drives.

Eric

I can tell you with certainty that the Mythbuntu 12.04.2 64-bit ISO can be used to create a bootable USB flash drive as I had to do a reinstall of my OS drive (due to hard drive failure) only a few weeks ago and this is precisely (no pun intended) how I installed it. I have not installed from CD/DVD in a few years.

I used "Startup Disk Creator" to create the bootable USB drive (see links below).

[https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu)
[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

---

### Post by tgm4883 on 2013-03-13
> **neutron68 said:**
> PLEASE...If the 12.04.02 64-bit ISO file only fits on a DVD-R, can it be noted out on the download page, to prevent confusion?
[http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads)


I've added a note under troubleshooting on the downloads page.

---

### Post by neutron68 on 2013-03-13
> **tgm4883 said:**
> I've added a note under troubleshooting on the downloads page.
Thanks for making that notation.

Eric

---

### Post by neutron68 on 2013-03-13
> **tgm4883 said:**
> I can tell you with certainty that the Mythbuntu 12.04.2 64-bit ISO can be used to create a bootable USB flash drive as I had to do a reinstall of my OS drive (due to hard drive failure) only a few weeks ago and this is precisely (no pun intended) how I installed it. I have not installed from CD/DVD in a few years.

I used "Startup Disk Creator" to create the bootable USB drive (see links below).

[https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu)
[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

Since the Mythbuntu 11.10 32-bit CD destroyed my Mythbuntu machine on Super Bowl night, I don't have a Ubuntu machine which I can run "Startup Disk Creator" on....a "egg before the chicken" problem.  So, I need a way to make a bootable USB Flash drive in Windows.

I'll start a new thread on this topic...

---

### Post by tgm4883 on 2013-03-13
> **neutron68 said:**
> Since the Mythbuntu 11.10 32-bit CD destroyed my Mythbuntu machine on Super Bowl night.

How did that happen.

---

### Post by neutron68 on 2013-03-13
The history is here:  [http://ubuntuforums.org/showthread.php?t=2112144](http://ubuntuforums.org/showthread.php?t=2112144)

The machine won't boot into Mythbuntu any more, so I've got to start from scratch.  I plan to load 12.04.2 64-bit.

---

### Post by neutron68 on 2013-03-13
In the name of closure:

I just got the Universal USB Installer (Pendrivelinux) to create a working bootable USB Flash drive!
I remade the USB flash drive and it worked this time. I'm not sure why it didn't work the first time.
I wonder if I "fat-fingered" the distro choice box when I made the first one??

Sorry for the false alarm!

I just used the Pendrivelinux USB flash drive to install the Mythbuntu 12.04.2 64-bit ISO image.  
I'm now tweaking the network settings and loading my favorite apps on the system!

Here we go...in 64-bits!!
Eric

---

