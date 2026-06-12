---
title: "Noob needing advice"
date: 2008-02-23
forum: Mythbuntu
---

### Post by Lutiana on 2008-02-23
Ok guys.

I have been running Windows MCE 2005 for quite sometime, but have decided that there must be something better so I am interested in trying out Mythbuntu.

I am not ridiculously familiar with linux, but can find my way around and can follow instructions well.

So here goes my plea for help and advice...

**_Heres what I want to be able to do _**(listed in order of priority):

1. Play digital video (mp4, divx) content from my windows server (Server 2003 running Active directory). This is my primary use as I download TV episodes, archive DVDs etc and store all of them on a windows share on my 2 TB server.

2. Watch vodcasts of some webshows (Tekzilla for example), so an RSS reader would be good.

3. Play emulated games (NES, SNES, SEGA Saturn, N64 etc) 

4. Play DVDs, preferably all zones since my family send me some DVDs from time to time. I haved used Slysofts AnyDVD for this on a windows machine, it works great.

5. Timeshift and record TV (NTSC for now, but ATSC when I get my new HD TV sometime this year). I would store all of this on the mythbuntu hardware. 

6. Eventually I will want to use some additional front ends in some other rooms, but for now I want to use just one machine.

And I would like to do all of this from my couch on my TV with a remote (and game pad where applicable). Also this will be a dedicated machine that will do nothing else.

**_What I have to do this with:_**

Dell Dimension 8300 (P4 3.0 w/ 1gb RAM, 160gb SATA HDD, DVD-RW)
Pinnacle PCTV HD PCI Card (800i)
Microsoft MCE Remote (not sure wich version)
VGA to Component convertor (not sure who makes it or its brand, but  it has worked acceptably so far).
A network infrastructure, complete with Active directory, high speed internet, smoothwall router (used as a DHCP and time server), linksys wireless access point and all hooked up with gigabit switches.

[B][U]
What I need before I embark on this:[/U][/B]

1. Advice
2. Howtos (as the standard ones do not go into the details of exactly what I need)
3. Any other information that may be relevant (ie what pitfalls to avoid).
4. A stiff drink

Any help will be geatly appreciated and any specific instructions more so.

---

### Post by ciprian_dimofte on 2008-02-23
I don't think that's such a good idea...

---

### Post by Tr1p on 2008-02-23
its possible but not when u use it for the first time

---

### Post by mwc on 2008-02-23
MythTV will do all you have asked, just install it and take it from there. I'd like to advise you on integration with your MS server but fortunately have not had to deal with Windows or Windows networks for about 5 years now:)

---

### Post by newlinux on 2008-02-23
> **mwc said:**
> MythTV will do all you have asked, just install it and take it from there. I'd like to advise you on integration with your MS server but fortunately have not had to deal with Windows or Windows networks for about 5 years now:)

Linux should have no problem sharing with your windows server and working well with your windows network, and can do all that you ask. It may take you a bit to get it perfect.

What kind of video card do you have? ATI are often problems in Linux. Also, I don't know much about that tuner card, but make sure it is supported in Linux.

How-tos:

Mythgame [http://www.mythtv.org/wiki/index.php/Configuring_MythGame_Emulation](http://www.mythtv.org/wiki/index.php/Configuring_MythGame_Emulation)

Mounting samba shares from your windows server:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

When you go to multiple frontends, make sure to mount things in the same place on each frontend or mythvideo (for watching your mp4s, divx, etc.) will not work right on each frontend.

What are you not finding in the how-tos that you need to know? It would be easier to help you if we knew specifically where you need help.

---

### Post by Tr1p on 2008-02-23
with those requirements is mythbuntu not enough btw

---

### Post by Lutiana on 2008-02-23
> **newlinux said:**
> What kind of video card do you have? ATI are often problems in Linux. Also, I don't know much about that tuner card, but make sure it is supported in Linux.

Iin that machine I have put in a Nvidia GeForce 6200LE (128Mb). Nvidia all the way!!!!

> **newlinux said:**
> Also, I don't know much about that tuner card, but make sure it is supported in Linux.


I did look up my tuner card and it does say that it is supported, it does not do hardware Mpeg2 encoding though. What kind of performance can I expect with this rig? MCE's performance on this machine was horrible (specifically the TV side).

> **newlinux said:**
>  When you go to multiple frontends, make sure to mount things in the same place on each frontend or mythvideo (for watching your mp4s, divx, etc.) will not work right on each frontend..

I am not sure what you mean by this, but I will keep it in mind, and hopefully it will make more sense when I get to that point.

> **newlinux said:**
> What are you not finding in the how-tos that you need to know? It would be easier to help you if we knew specifically where you need help.


The two you listed are perfect for now, but one on how to install codecs would be good. And will Mythbuntu play DVDs out the box? If not a howto on making DVDs work would be good.

So based on all the info I got here  I am going to attempt to install Mythbuntu today, since I think it will do what I want/need. I am sure that once my feet are wet then I will have a ton more questions, but I will deal with them when I get there.

---

### Post by newlinux on 2008-02-23
You'll learn about the mounting soon enough. I don't know about the quality of the signal from that tuner card, but performance wise that should do quite well. My main home-desktop is a P4 2.6Ghz HT with a Geforce MX440 and it goes as fast as I want for most tasks (no noticeable difference from my X2 3800 and X2 4200) and can even playback 720P HD in myth (it's also a backend/frontend myth machine). Transcoding and commercial flagging take a bit longer though, but everyday tasks great.

[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

for dvd playback and multimedia codecs.

---

### Post by Lutiana on 2008-02-23
Okay, so after some more research about this card I found this:
[http://mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

If I am reading this right, then I am going to have to add the driver for it after the install of the OS. Am I right? 

If this is the case, then how exactly do I install the driver. The instructions on LinuxTV are not very clear to me.

---

### Post by newlinux on 2008-02-24
looks like you need firmware and a driver... Firmware is a matter of running the extraction script on the windows driver and then with sudo priveleges copying the resulting file to the /lib/firmware directory.

looks like you download the driver tarball and unpack it (you can use archive manager to do this or do it commandline with the tar command). Then cd into the unpacked directory and type ```
make
``` and then type ```
make install
``` (this compiles and copies the files to the right directories - which is installing the driver).

[http://linuxtv.org/repo/](http://linuxtv.org/repo/) 

gives good instructions for this.

---

### Post by Lutiana on 2008-02-24
> **Lutiana said:**
> 

**_Heres what I want to be able to do _**(listed in order of priority):

1. Play digital video (mp4, divx) content from my windows server (Server 2003 running Active directory). This is my primary use as I download TV episodes, archive DVDs etc and store all of them on a windows share on my 2 TB server.



Done, mapped windows share to /mnt/windows, and it seem that Mythbuntu come pre-packaged with all the codecs I need. I have tested about a dozen of my videos and they all seem to work just fine. 

> **Lutiana said:**
> 

2. Watch vodcasts of some webshows (Tekzilla for example), so an RSS reader would be good.



Mythbuntu also does this out the door. Added Tekzilla and it works well. 

I am still working on the rest of the list, but I will resume this another day.

---

### Post by Lutiana on 2008-02-24
> **newlinux said:**
> looks like you need firmware and a driver... Firmware is a matter of running the extraction script on the windows driver and then with sudo priveleges copying the resulting file to the /lib/firmware directory.

looks like you download the driver tarball and unpack it (you can use archive manager to do this or do it commandline with the tar command). Then cd into the unpacked directory and type ```
make
``` and then type ```
make install
``` (this compiles and copies the files to the right directories - which is installing the driver).

[http://linuxtv.org/repo/](http://linuxtv.org/repo/) 

gives good instructions for this.

Okay, I managed to get the firmware extracted and placed on the right directory, downloade the gziped tar ball and extracted this. But when I try to make this I get this:

```

make -C /tmp/v4l-dvb/v4l 
make[1]: Entering directory `/tmp/v4l-dvb/v4l'
No version yet, using 2.6.22-14-generic
make[1]: Leaving directory `/tmp/v4l-dvb/v4l'
make[1]: Entering directory `/tmp/v4l-dvb/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.22
File not found: /lib/modules/2.6.22-14-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: Leaving directory `/tmp/v4l-dvb/v4l'
make[1]: Entering directory `/tmp/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.22
File not found: /lib/modules/2.6.22-14-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/tmp/v4l-dvb/v4l'
make: *** [all] Error 2
```

Suffice to say make install does not work either.

I have no idea where to go from here.

---

### Post by Lutiana on 2008-02-25
I got this solution from a different forum and it helped fix the issue.

> **pops66 said:**
> It almost looks like you may not have all the kernel headers installed. Look for and install something along the lines of linux-headers-generic.


I installed (via synaptics) linux-headers-generic and the ones for my kernel version.

Now all I need to do is get VNC to work. It was working 100% till I changed my X-resolution to 1024x768 (for my TV) and now when I connect all I get is a scrambled screen on the client side. 

Any ideas?

---

