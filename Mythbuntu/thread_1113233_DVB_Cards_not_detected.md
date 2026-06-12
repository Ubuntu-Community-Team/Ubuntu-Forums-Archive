---
title: "DVB Cards not detected"
date: 2009-04-01
forum: Mythbuntu
---

### Post by mekis on 2009-04-01
I used to run a Mythbuntu 8.04, where I had a LifeView DVB-S, an old Twinhan DVB-T and a Hauppauge Nova-T-500 dual receivers all four working fine. Now I need to convert the machin to an all purpose server and tried a clean install of Ubuntu Server 8.10 (so I might be in the wrong forum now)
:lolflag:

I did a fresh install of MythTv 0.21, checked the database and permissions, and finaly entered mythtv setup. In the Capture Card Setup I changed the Card type to DVB DTV capture card and expected to find the cards as DVB Device Number 0 to 3 But the result was Frontend ID: Could not get card info!

Then I checked dmesg and found the cards as frontend 0, LifeView, 1 Twinhan, 2 and 3 Hauppauge.

Could anyone plese give ma a clou to where to search or to how I can fix this because I am lost.

---

### Post by nickrout on 2009-04-01
Does the server kernel have dvb drivers?

```
dmesg|grep -i dvb
``` will tell if they are detected.

---

### Post by mekis on 2009-04-02
Thank you nickrout for trying to help me.

I tried dmesg|grep -i dvb and all four receivers are detected so the kernel have DVB drivers loaded. This is what it looks like:

```

[    7.582555] saa7134[0]: subsystem: 5168:0300, board: LifeView FlyDVB-S /Acorp TV134DS [card=97,autodetected]
[    7.582610] input: saa7134 IR (LifeView FlyDVB-S / as /devices/pci0000:00/0000:00:1e.0/0000:04:01.0/input/input5
[    7.728484] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[    7.728486] firmware: requesting dvb-usb-dib0700-1.10.fw
[    7.803400] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[    7.803443] bttv0: add subdevice "dvb0"
[    7.912562] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[    8.051260] DVB: registering new adapter (saa7134[0])
[    8.051263] DVB: registering frontend 0 (Philips TDA10086 DVB-S)...
[    8.401582] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[    8.946926] DVB: registering new adapter (bttv0)
[    9.110038] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[    9.110072] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    9.110197] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[    9.239801] DVB: registering frontend 2 (DiBcom 3000MC/P)...
[    9.297142] DVB: registering frontend 1 (DST DVB-T)...
[    9.857349] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    9.857525] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[    9.863351] DVB: registering frontend 3 (DiBcom 3000MC/P)...
[   10.469328] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/usb8/8-1/input/input7
[   10.491313] dvb-usb: schedule remote query interval to 150 msecs.
[   10.491317] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   10.491541] usbcore: registered new interface driver dvb_usb_dib0700

```

As far as I can tell this looks OK.

---

### Post by nasha on 2009-04-02
This might be a long shot, but i had a similar issue... Whether the causes are the same is totally different lol
But are there any firmware files required for those cards, and have you copied the across?
This was my solution anyway, hope it helps lol

---

### Post by mekis on 2009-04-02
Thank you nasha for your help. The Hauppauge card needs special firmware, dvb-usb-dib0700-1.10, which is loaded according to dmesg but the other two, Twinhan and LifeView, doesn't need any special firmware.

So unfortunately this wasn't the sollution to my problem.

---

### Post by mekis on 2009-04-08
I solved the problem with the help of MythTV support group.

My misstake was trying to do the setup as another user than mythtv and that user did not have permission to read /dev/dvb/adapterN/*. The permission for these catalouges was rw for owner root and group video. User mythtv was member of group video but the user I tried to use for setup did not have that permission.

Sollution: add the user I am using to group video.

Hope this helps someone else trying to do something similar.

---

