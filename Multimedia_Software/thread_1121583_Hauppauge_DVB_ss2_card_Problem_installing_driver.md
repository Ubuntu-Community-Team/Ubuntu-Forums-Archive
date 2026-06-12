---
title: "Hauppauge DVB s/s2 card: Problem installing driver"
date: 2009-04-10
forum: Multimedia Software
---

### Post by technoboi on 2009-04-10
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"
GNU/Linux 2.6.24-23-generic
'Build Essential' is installed. Reports as latest version.

I am trying to install a Hauppauge Satellite DVB S/S2 card on my Mythtv box.
I have succeeded in downloading the necessary firmware but the driver is
proving a problem. I have tried 2 different information sources, for set up, but both give the same problem. 

I have, btw, done a full system update and upgrade.

As you will see below, or at least this is how I interpret it, the 'make'
tries to create a file called .config - I assume from the error reported
that it is supposed to locate this in
/lib/modules/2.6.24-23-generic/build/   There wasn't a build directory, so lest this was the fault, I created one....but that didn't help. I can't
find this config file and I don't know how to proceed from here.
.......................
brian@MC:/usr/local/src/v4l-dvb/v4l$ ls
compat.h      Kconfig.sound    Makefile.kernel  obsolete.txt
firmware      Makefile         Makefile.media   scripts
i2c-compat.h  Makefile.kern24  Makefile.sound   versions.txt
brian@MC:/usr/local/src/v4l-dvb/v4l$ sudo make Updating/Creating
.config Preparing to compile for kernel version 2.6.24 File not found:
/lib/modules/2.6.24-23-generic/build/.config at ./scripts/make_kconfig.pl
line 32, <IN> line 4.
make: *** No rule to make target `.myconfig', needed by `config-compat.h'.
Stop.
brian@MC:/usr/local/src/v4l-dvb/v4l$
...................

Has anyone any ideas on this one?

---

### Post by mymythtv on 2009-05-04
Hi

Not quite sure if I got the same card ( got a Nova-S2 ), but I got it working

Currently running:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

You are on 8.04, so maybe a "do-release-upgrade" will bring you to 8.10.
Then I downloaded latest driver and compiled from
[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Basicly I did:
hg clone  [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
make
make install

It will then recognize the card ( hopefully ). I got a WinTV-HVR4000(Lite) - aka Nova-S2

You find info by typing: dmesg | grep dvb
Mine looks like:
cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1

My firmware is: /lib/firmware/dvb-fe-cx24116-1.23.86.1.fw

Good luck

---

### Post by technoboi on 2009-05-06
> **mymythtv said:**
> Hi

Not quite sure if I got the same card ( got a Nova-S2 ), but I got it working

Currently running:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

You are on 8.04, so maybe a "do-release-upgrade" will bring you to 8.10.
Then I downloaded latest driver and compiled from
[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Basicly I did:
hg clone  [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
make
make install

It will then recognize the card ( hopefully ). I got a WinTV-HVR4000(Lite) - aka Nova-S2

You find info by typing: dmesg | grep dvb
Mine looks like:
cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1

My firmware is: /lib/firmware/dvb-fe-cx24116-1.23.86.1.fw

Good luck
Thanks for your reply.
I was interested to know how to upgrade to 8.10 (and now we can upgrade that to 9.1 of course, I have done that on my main computer).
 I should have come back and posted my progress. 
I didn't realise that the linux headers weren't installed by default. Once installed I was able to complete the installation of the driver. I can get the card working now in mplayer. However, sadly, that isn't the end of the story because now I can't get it to work with MythTV. I made a channels.conf file but MythTV doesn't want to scan it and it won't do a tuning scan either.I tried the tuning scan with the first setting being BBC 1 London. I have since even tried uninstalling and reinstalling MythTV to no avail. My LNB is set up appropriately. 
Whilst I can be sure the firmware installation must be OK, as the card works in mplayer, I don't know if the driver I installed is used when using mplayer or not.I am assuming it is.
So now I am stuck!! :-(

---

