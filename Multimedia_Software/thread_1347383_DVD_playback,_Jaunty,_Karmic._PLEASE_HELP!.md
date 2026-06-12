---
title: "DVD playback, Jaunty, Karmic. PLEASE HELP!"
date: 2009-12-06
forum: Multimedia Software
---

### Post by dogscoff on 2009-12-06
I have been having trouble with DVD playback since Jaunty. Yesterday I reinstalled from scratch, using Karmic, in the hope that it would fix things. It hasn't. I've posted here numerous times, and filed a bug report. Nobody seems to be interested. Could someone please help.

I have already installed libdvdcss2, libdvd4, libdvdnav, ffmpeg, all the gstreamer stuff. It's a 64 bit install.

When I put a DVD in the drive, there is about a 50/50 chance that it won't work. It clonks and gronks and nothing happens. Ubuntu doesn't even seem to recognise that there is a disc in the drive, nothing shows up in the "computer" window. If I open VLC and tell it to open the DVD, it says "playback failure: DVDread could not open the disc/dev/sr0". Your input can't be opened. VLC is unable to open the MRL DVD "dvd:///dev/sr0. Check the log for details."

Other DVDs work just fine, so the drive can't be faulty. The DVDs themselves are fine, they work in other machines and used to work in this one before Jaunty. I'm seriously considering a return to Intrepid. 

I can post more info if needs be.

---

### Post by Sairin_Lote on 2009-12-12
hey, i had the same problem and i fixed it doing:


```
sudo wget http://www.medibuntu.org/sources.list.d/karmic.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get update && sudo apt-get upgrade

sudo apt-get -y install libdvdcss2 libdvdread4 libdvdnav4 amrnb amrwb libamrnb3 libamrwb3 aacgain non-free-codecs ubuntu-restricted-extras
```

My box is Ubuntu 9.10 i686. Hope it helps

---

### Post by Lain_Noskire on 2009-12-13
[SIZE=3](Using Karmic amd 64) I was also having this problem too. Did everything from installing drivers to modifying files. I've found one thing that worked (after installing drivers ofcourse). It was found when messing around with splash screens (and failing). I found device.map and in it was just this:

[I](hd0)    /dev/sda
(hd1)    /dev/sdb[/I]

I recognized these as the hard drive so I:

[I]sudo gedit /boot/grub/device.map

[/I]entered the line:

*(cdrom) /dev/dvdrw  *(knew this from* sudo lshw -C disk*)

saved 

*sudo update-grub *(<--don't know if that actually helped since i was still messing with the splashscreens i would like help with those btw)

reboot

put in a dvd and it worked.
[/SIZE]

---

