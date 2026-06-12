---
title: "Cannot recognize Hauppauge HVR 2250; have installed firmware numerous times..."
date: 2014-03-10
forum: Mythbuntu
---

### Post by tbsoft2001 on 2014-03-10
Hello. Here is the output:

```

user@user:~$ dmesg | grep saa7164
[    7.716616] saa7164 driver loaded
[    7.717182] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    7.717189] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfdc00000
[    7.873672] saa7164_downloadfirmware() no first image
[    7.873734] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    8.135009] saa7164_downloadfirmware() Upload failed. (file not found?)

```

I have downloaded the NXP7164-2010-03-10.1fw numerous times; say, maybe 10.
 
Copied it to /lib/firmware.
 
Copied it to /lib/firmware/3.*generic.

Tried every other potential fix I could find including

```

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
http://www.steventoth.net/linux/hvr22xx/extract.sh
sh extract.sh
cp *fw /lib/firmware

```

Really, I think the problem is that, for some reason, my system will not download and install that NXP7164* firmware - and for the life of me, I don't know why.

This is the info about the myth install:

```

user@user:~$ mythfrontend --version
Please attach all output as a file in bug reports.
MythTV Version : v0.25.2-15-g46cab93
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120506-1
QT Version : 4.8.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_iptv using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libxml2 using_lirc using_mheg using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_live using_mheg using_libass using_libxml2

```

Thinking I might be clever I purged the mythtv install from the mythbuntu installation (which is what I originally installed v. 12.04.3-64 bit version) and then reinstalled mythtv from synaptic. Looks different; acts exactly the same.

```

user@username:~$ uname -a
Linux username 3.8.0-37-generic #53~precise1-Ubuntu SMP Wed Feb 19 21:37:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```



I've spent at least 5 hours attempting to configure this. Yes, I'm fed up.

---

### Post by tbsoft2001 on 2014-03-12
I marked this thread as "solved" even though I didn't find a solution - well, I did, but it had nothing to do with Mythbuntu or LTS12.04 etc....

On a hunch, I installed Linux Mint 16 Petra, 64-bit. I downloaded the driver for the Hauppauge 2250, placed it in /lib/firmware, rebooted, and the card was recognized and the firmware update applied - the thing i could never get to happen using Ubuntu 12... first try.

this is the second project in six weeks in which I've abandoned 12.04. I built a media server and 12.04 was giving me problems so I went with 13.10 server - worked right the first time. I don't remember the problem but I had enough sense not to waste hours attempting to get it to work - sometimes it's simply wiser, I've found, to move on instead of spending hours reading posts from people who had similar problems ---- and getting nowhere.

Anyway, if you're having problems with the 2250 and you can't resolve them - find another version of linux which will work without the hassle.

Time is precious. Don't waste it on a stupid Ubuntu install.

---

