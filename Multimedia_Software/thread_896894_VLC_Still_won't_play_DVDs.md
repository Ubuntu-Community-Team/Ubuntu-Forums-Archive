---
title: "VLC Still won't play DVDs"
date: 2008-08-21
forum: Multimedia Software
---

### Post by coachher on 2008-08-21
Hi, 

I've been trying to get DVD playback working on my ThinkPad T61 running a fresh install of Ubuntu Hardy 8.04. I've tried a whole bunch of tutorials including the sticky on the front page of the forum and the guide on the Medibuntu wiki ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) and by running install-css.sh ([http://ubuntu-tutorials.com/2008/07/01/enable-commercial-dvd-playback-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/07/01/enable-commercial-dvd-playback-on-ubuntu-804/)). I've searched the forums high and low and all the threads seem to have slightly different versions of the same 

Anyway. here's the latest output from vlc when I run it from the console

[INDENT]>> vlc dvd:///media/cdrom
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/kochhar/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000136
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00005bdf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000b9bb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00194d3d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001ad993
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00347000
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
[00000283] main playlist: nothing to play
[/INDENT]

Any help on what to do next would be greatly appreciated. I can also post the output of vlc --verbose 2 if you'd like.

---

### Post by mc4man on 2008-08-21
First do you know if a region has been set on the drive?
If not sure ck. here.
[http://ubuntuforums.org/showthread.php?p=5451540#post5451540](http://ubuntuforums.org/showthread.php?p=5451540#post5451540)

Open vlc fron the terminal with just vlc and then go file -> open disk. Use dev/scd0 in the device box. That way you should be able to see dvd title info and not get this.
> libdvdnav: Can't read name block. Probably not a DVD-ROM device. Note the above line is not a problem, it's just not as informative as it could be. 

On laptops it's also good to know the model of dvd drive
sudo lshw -C disk will show

---

### Post by silkstone on 2008-08-21
Are you sure you have libdvdcss2 from the Medibuntu repos, and not just libdvdcss?

If not, enable Medibuntu and install libdvdcss2...

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get install libdvdcss2
```

---

### Post by coachher on 2008-08-21
I did set the region to region 1. It wasn't that. Apparently there is a new form of copy protection that some movies are using and there is a bug to that effect in libdvdnav where it decrypts the disc incorrectly. Anyway, this forum post was most helpful in getting things working again. I think I might have stumbled across it earlier and tried it but it didn't work. This time around I had deleted the contents of the .dvdcss folder in my home directory and Voila! Things work again.

I think this entire rigmarole could have been avoided if the DVD drivers were installed automagically the first time you log in without the need for many many sets of instructions. 

Just my $0.02. 

Thanks for all your replies though. The active community really warms my heart.

---

### Post by coachher on 2008-08-21
The actual patched deb archives are available here:
[http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)

Follow the instructions for i386 binaries. Though the repositories are for debian, they work fine with ubuntu Hardy. I used the debian stable versions.

Once again, thanks.

---

### Post by mc4man on 2008-08-21
this new dvdnav has the patch incorporated in it, been using it for a few weeks with no issues
[http://packages.debian.org/lenny/libdvdnav4](http://packages.debian.org/lenny/libdvdnav4)

If you want to install just  let gdebi handle, no need to remove current ver. first. (no players removed)

expect to see it in 8.10 as default dvdnav ver.

mplayer still needs patched dvdread in source before building

---

