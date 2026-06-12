---
title: "hvr-1600 difficulties"
date: 2009-10-25
forum: Mythbuntu
---

### Post by zapstrap on 2009-10-25
I have mythbuntu 9.04, (linux kernel 2.6.28-15) and have been running it with a hauppauge pvr-150 and an nvidia geforce 6200 card (proprietary drivers) for several months now.  I just added a hauppauge hvr-1600, and am having no success.

At first power-up with the new card installed, the nvidia driver broke, but I had read about a kernel issue with the hvr-1600 and nvidia cards.  I added vmalloc=256m to the kernel load line in /boot/grub/menu.lst with good results.

At this point, I loaded the myth backend configuration tool and tried to configure the second tuner card.  The card couldn't be found.  I then assumed the drivers weren't loaded, and went here:

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

I followed the directions, and when I run dmesg | grep cx18, I get this:

```

[    6.978608] cx18:  Start initialization, version 1.2.0
[    7.127313] cx18-0: Initializing card 0
[    7.127320] cx18-0: Autodetected Hauppauge card
[    7.132859] cx18 0000:02:0c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    7.137970] cx18-0: cx23418 revision 01010000 (B)
[    7.341456] cx18-0: Autodetected Hauppauge HVR-1600
[    7.341459] cx18-0: Simultaneous Digital and Analog TV capture supported
[    7.457979] tuner 2-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[    7.475491] tuner 2-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[    7.482791] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[    7.486271] cx18-0: Registered device video1 for encoder MPEG (64 x 32 kB)
[    7.486278] DVB: registering new adapter (cx18)
[    7.604179] cx18-0: DVB Frontend registered
[    7.604184] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[    7.604235] cx18-0: Registered device video33 for encoder YUV (16 x 128 kB)
[    7.604281] cx18-0: Registered device vbi1 for encoder VBI (20 x 51984 bytes)
[    7.604334] cx18-0: Registered device video25 for encoder PCM audio (256 x 4 kB)
[    7.604384] cx18-0: Registered device radio1 for encoder radio
[    7.604389] cx18-0: Initialized card: Hauppauge HVR-1600
[    7.604420] cx18:  End initialization
[   20.780300] cx18 0000:02:0c.0: firmware: requesting v4l-cx23418-cpu.fw
[   20.976483] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   21.001541] cx18 0000:02:0c.0: firmware: requesting v4l-cx23418-apu.fw
[   21.115218] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   21.924014] cx18-0: Could not start the CPU
[   21.924020] cx18-0: Retry loading firmware
[   21.928524] cx18 0000:02:0c.0: firmware: requesting v4l-cx23418-cpu.fw
[   22.044442] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   22.068714] cx18 0000:02:0c.0: firmware: requesting v4l-cx23418-apu.fw
[   22.173498] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   22.972031] cx18-0: Could not start the CPU
[   22.972038] cx18-0: Failed to initialize on minor 8
[   22.972053] cx18-0: Failed to initialize on minor 6
[   22.972556] cx18-0: Failed to initialize on minor 4
[   22.972913] cx18-0: Failed to initialize on minor 7
[   22.973265] cx18-0: Failed to initialize on minor 5
[   28.911014] cx18-0: Failed to initialize on minor 4

```No matter what I do, I can't get the CPU on the hvr-1600 to start.  I tried moving the card to a new pci slot.  The pvr-150 is still in the machine.  What am I doing wrong?

---

### Post by dano1 on 2009-10-25
You've tried a reboot(or 2) and a cold boot? try rebuilding v4l.

see also : [http://ivtvdriver.org/index.php/Cx18](http://ivtvdriver.org/index.php/Cx18)
basically same info but something may help.

---

### Post by zapstrap on 2009-10-26
Oh yes, I even tried turning the power switch off on the back of the case.  I tried pulling the pvr-150 out, no change.  I admit I didn't try building v4l a second time, but I thought building it once would be sufficient.  I'll give it a go next time (next weekend).  In the mean time, I'm suspicious of the hvr-1600 card.  Does anyone know if there's a diagnostic suite for this?  I didn't see one on Hauppauge's web-site or their ftp server.  I tried putting this card into a winxp box, and the driver installed fine, but after an hour of futzing about I got nowhere.  I tried vlc and wintv.  WinTV wouldn't even start.  I felt I was having better luck on the mythbuntu machine, at least there I could see the card was being initialized.

---

### Post by dano1 on 2009-10-26
not that im aware of. havent had a prob with my 1600. may be a bad card as u said if ur having probs in windows also. Might try dscaler(windows app,only sees the anaolog side) theres very little setup involved.

hth, danny

---

### Post by bsntech on 2009-10-26
It unfortunately does sound like a hardware issue.  Did you buy the card off of eBay or purchase it new?  Sometimes folks sell junk that doesn't work on eBay - I've been lucky so far to get things that work - although I've had a few issues sometimes.

If you tried it with the Windows drivers and still couldn't get it to work - I think this is the tell-tale sign it seems to be hardware.

In addition, when I had Ubuntu 9.04, I just installed the HVR-1600 (I also had a PVR-150 like you do) - and it just worked...

However, if you want to try this last thing before returning the card, it is easier to recompile the v4l-dvb drivers using mercurial.

sudo apt-get install mercurial
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
sudo make
sudo make install

Then reboot.  This will update you to the newest v4l-dvb drivers available from the website.

---

### Post by zapstrap on 2009-10-29
Hmm, I already did all that, this should work.  OK, everybody loves a story, so here's how this one ends:

Phoned Hauppauge, and got them to walk me through installing the card in a windows xp machine.  I figured asking for support with an ubuntu installation wouldn't go far.  The card shows in the device list, and once the tv tuner app was installed, I could search for and find channels.  The app would not display any video.  Like a typical idiot, I tried again in a second windows xp machine with the same results.  It's a good thing I'm not stubborn.  Imagine the peanut in my cranium receiving the message...dead hardware sparky...send it back to the half-wit on e-bay that sold it to you...post negative feedback because he said it was new...it isn't...and is broken...loser.  In fairness, he gave me an rma with little fuss, so he's not a total loser, only partially.

Moving on, ordered the same card from NCIX locally, for almost the same price.  It showed up today.  I stuck it in the myth box, and...it works, 1st try.  Relieved, but there must be a wall around here somewhere I can beat my head against...8 hours on Sunday fighting, another 90 minutes on the phone with Hauppauge...gah!

OK I feel better now that I've griped, sorry if I've offended anyone.

On the upside, all that effort meant that once I did drop the new card in, I could immediately check dmesg for the any cx18 messages, and determine within a few seconds that all's well and I'm off to the races.

---

