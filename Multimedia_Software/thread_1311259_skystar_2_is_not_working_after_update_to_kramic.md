---
title: "skystar 2 is not working after update to kramic"
date: 2009-11-02
forum: Multimedia Software
---

### Post by netlord on 2009-11-02
hi there

can anyone help me? i´min trouble with an skystar 2-card which is not longer working after updating to karmic.

ubuntu seems to recognise the card itself
> chriss@solaris:~/script$ dmesg | grep SkyStar
[   21.770227] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
chriss@solaris:~/script$ dmesg | grep b2c2
[   20.882639] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   20.889415] b2c2_flexcop_pci 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[   20.931820] b2c2-flexcop: MAC address = 00:d0:d7:13:19:68
[   21.770155] b2c2-flexcop: found 'ST STV0299 DVB-S' .
[   21.770227] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete

> chriss@solaris:~/script$ ls /dev/dvb/adapter0 -ali
insgesamt 0
6617 drwxr-xr-x  2 root root     120 2009-11-02 15:40 .
6616 drwxr-xr-x  3 root root      60 2009-11-02 15:40 ..
6621 crw-rw----  1 root video 212, 6 2009-11-02 15:40 ca0
6619 crw-rw----+ 1 root video 212, 4 2009-11-02 15:40 demux0
6620 crw-rw----+ 1 root video 212, 5 2009-11-02 15:40 dvr0
6618 crw-rw----+ 1 root video 212, 3 2009-11-02 15:40 frontend0


but neither kaffeine or me-tv seems to recognise the device, so it isnt wroking.

i already set up the card using this this wiki: [http://wiki.ubuntuusers.de/B2C2](http://wiki.ubuntuusers.de/B2C2), but....

anyone an idea?

---

### Post by hoani.cross on 2009-11-15
Hi,

I also have a Technisat SkyStar 2 TV PCI card under Karmic Koala with a ATI Radeon 9550 (radeon driver). I currently have issues with playing TV under mythtv, the sound was working but the video only display 1 line (I can see images moving either). I thought that it was a problem with the driver of the DVB card so I decided to go further.

When checking the technisat website, I saw that they provide a proprietary driver using the v4l-dvb tree. In the release, they asked to retreive a specific version of the v4l-dvb tree to be patched with diff patches and a precompiled blob object. I followed instructions but I failed on a compilation error... since the tree to get was dated of year 2008, I thought that there would be huge differences with the current karmic v4l-dvb selected tree. I thus tried to get the LATEST tree for the v4l website, apply the patches manually (the markers where not totally equals) and start compiling. Compilation succeeded, as module installation but loading the modules throws many dmesg errors (unknown symbols) which rely on version diff between the LATEST v4l-dvb and Karmic v4l-dvb trees, but it loads anyway :)

Next time if I want to go in this way, I should get the v4l-dvb tree used in the current Karmic kernel.

I could get into mythtv and start earing the sound with video displayed on one line only :( still stuck at the same place, it wasn't a card problem (today I know my problem rely on [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898)).

I also tested Kaffeine BEFORE and AFTER compiling v4l-dvb with the same result as you : "no suitable device found".

Hopes this will give you some directions.

---

