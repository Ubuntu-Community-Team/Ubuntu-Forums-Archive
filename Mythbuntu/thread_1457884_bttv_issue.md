---
title: "bttv issue"
date: 2010-04-19
forum: Mythbuntu
---

### Post by sqeelurgle on 2010-04-19
I have another thread about my bot issue, but it looks like a more specific problem - there seems to be a problem with bttv - or bt878.  I have a few logs here,

From a god boot:

from message.log

> Apr 19 21:28:56 peter-desktop kernel: [   20.024020] tda10048_firmware_upload: firmware uploaded
Apr 19 21:28:56 peter-desktop kernel: [   20.219111] type=1503 audit(1271676536.744:20): operation="open" pid=1200 parent=1199 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Apr 19 21:28:57 peter-desktop kernel: [   21.346278] type=1503 audit(1271676537.872:21): operation="open" pid=1230 parent=1229 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Apr 19 21:28:58 peter-desktop kernel: [   22.227406] type=1503 audit(1271676538.752:22): operation="open" pid=1346 parent=1238 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Apr 19 21:28:59 peter-desktop kernel: [   22.577019] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
Apr 19 21:28:59 peter-desktop kernel: [   22.577038] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 19 21:28:59 peter-desktop kernel: [   22.577072] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 19 21:28:59 peter-desktop kernel: [   22.764102] type=1503 audit(1271676539.292:23): operation="open" pid=1352 parent=1351 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Apr 19 21:29:00 peter-desktop kernel: [   23.788777] type=1503 audit(1271676540.316:24): operation="open" pid=1367 parent=1366 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Apr 19 21:29:01 peter-desktop kernel: [   24.811294] type=1503 audit(1271676541.336:25): operation="open" pid=1380 parent=1379 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Apr 19 21:29:02 peter-desktop kernel: [   25.890437] type=1503 audit(1271676542.416:26): operation="open" pid=1397 parent=1396 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Apr 19 21:29:02 peter-desktop kernel: [   26.047142] type=1503 audit(1271676542.572:27): operation="open" pid=1412 parent=1411 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Apr 19 21:29:07 peter-desktop kernel: [   31.328066] tda18271: performing RF tracking filter calibration
Apr 19 21:29:12 peter-desktop kernel: [   35.960797] tda18271: RF tracking filter calibration complete
Apr 19 21:29:17 peter-desktop kernel: [   40.492094] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 131
Apr 19 21:29:47 peter-desktop kernel: [   70.482210] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 21:30:27 peter-desktop kernel: [  110.480757] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 131


From dmesg grep bt:
> 
[   10.402174] bttv: driver version 0.9.18 loaded
[   10.402179] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   10.402235] bttv: Bt8xx card found (0).
[   10.402588] bttv 0000:02:0a.0: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[   10.402599] bttv0: Bt878 (rev 17) at 0000:02:0a.0, irq: 17, latency: 64, mmio: 0xec7fe000
[   10.405602] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[   10.405608] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[   10.405612] IRQ 17/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.405652] bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
[   10.405890] bttv0: tuner absent
[   10.405929] bttv0: add subdevice "dvb0"
[   10.463304] bt878: AUDIO driver version 0.0.0 loaded
[   11.287007] bt878: Bt878 AUDIO function found (0).
[   11.287032] bt878 0000:02:0a.1: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[   11.287037] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[   11.287045] bt878(0): Bt878 (rev 17) at 02:0a.1, irq: 17, latency: 64, memory: 0xec7ff000
[   11.287068] IRQ 17/bt878: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.907476] DVB: registering new adapter (bttv0)


Now from a bad boot:

From message.log

> Apr 19 20:50:08 peter-desktop kernel: [   38.476086] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 131
Apr 19 20:50:10 peter-desktop kernel: [   41.184013] dvb_bt8xx: gave up waiting for init of module bt878.
Apr 19 20:50:10 peter-desktop kernel: [   41.184022] dvb_bt8xx: Unknown symbol bt878_num
Apr 19 20:50:38 peter-desktop kernel: [   68.476106] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:50:40 peter-desktop kernel: [   71.184012] dvb_bt8xx: gave up waiting for init of module bt878.
Apr 19 20:50:40 peter-desktop kernel: [   71.184021] dvb_bt8xx: Unknown symbol bt878_start
Apr 19 20:51:10 peter-desktop kernel: [  101.184012] dvb_bt8xx: gave up waiting for init of module bt878.
Apr 19 20:51:10 peter-desktop kernel: [  101.184071] dvb_bt8xx: Unknown symbol bt878_stop
Apr 19 20:51:18 peter-desktop kernel: [  108.474252] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:51:40 peter-desktop kernel: [  131.184013] dvb_bt8xx: gave up waiting for init of module bt878.
Apr 19 20:51:40 peter-desktop kernel: [  131.184072] dvb_bt8xx: Unknown symbol bt878
Apr 19 20:51:40 peter-desktop kernel: [  131.264358] Chip ID is not zero. It is not a TEA5767
Apr 19 20:51:40 peter-desktop kernel: [  131.264541] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
Apr 19 20:51:40 peter-desktop kernel: [  131.351162] saa7130[0]: registered device video0 [v4l2]
Apr 19 20:51:40 peter-desktop kernel: [  131.351239] saa7130[0]: registered device vbi0
Apr 19 20:51:40 peter-desktop kernel: [  131.351332] bt878: Bt878 AUDIO function found (0).
Apr 19 20:51:40 peter-desktop kernel: [  131.351397] bt878 0000:02:0a.1: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
Apr 19 20:51:40 peter-desktop kernel: [  131.351453] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Apr 19 20:51:40 peter-desktop kernel: [  131.351511] bt878(0): Bt878 (rev 17) at 02:0a.1, irq: 17, latency: 64, memory: 0xec7ff000
Apr 19 20:51:40 peter-desktop kernel: [  131.351637] IRQ 17/bt878: IRQF_DISABLED is not guaranteed on shared IRQs
Apr 19 20:51:40 peter-desktop kernel: [  131.417186] saa7134 ALSA driver for DMA sound loaded
Apr 19 20:51:40 peter-desktop kernel: [  131.417256] saa7130[0]/alsa: Leadtek Winfast DTV1000S doesn't support digital audio
Apr 19 20:51:40 peter-desktop kernel: [  131.426665] dvb_init() allocating 1 frontend
Apr 19 20:51:41 peter-desktop kernel: [  131.509421] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19
Apr 19 20:51:41 peter-desktop kernel: [  131.509495] ESS ES1938 (Solo-1) 0000:02:08.0: PCI INT A -> Link[LNKC] -> GSI 19 (level, low) -> IRQ 19
Apr 19 20:51:41 peter-desktop kernel: [  131.599340] gameport: ES1938 is pci0000:02:08.0/gameport0, io 0xac00, speed 59659kHz
Apr 19 20:51:41 peter-desktop kernel: [  131.692193] tda18271 2-0060: creating new instance
Apr 19 20:51:41 peter-desktop kernel: [  131.700031] TDA18271HD/C2 detected @ 2-0060
Apr 19 20:51:41 peter-desktop kernel: [  132.096011] DVB: registering new adapter (saa7130[0])
Apr 19 20:51:41 peter-desktop kernel: [  132.096083] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
Apr 19 20:51:41 peter-desktop kernel: [  132.424009] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
Apr 19 20:51:41 peter-desktop kernel: [  132.424103] saa7134 0000:02:09.0: firmware: requesting dvb-fe-tda10048-1.0.fw
Apr 19 20:51:42 peter-desktop kernel: [  132.472791] tda10048_firmware_upload: firmware read 24878 bytes.
Apr 19 20:51:42 peter-desktop kernel: [  132.472861] tda10048_firmware_upload: firmware uploading
Apr 19 20:51:46 peter-desktop kernel: [  136.644049] tda10048_firmware_upload: firmware uploaded
Apr 19 20:52:08 peter-desktop kernel: [  158.476090] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:53:08 peter-desktop kernel: [  218.473874] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:53:20 peter-desktop kernel: [  230.496057] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:53:20 peter-desktop kernel: [  230.496365] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
Apr 19 20:54:08 peter-desktop kernel: [  278.484063] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:54:26 peter-desktop kernel: [  296.515070] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Apr 19 20:54:31 peter-desktop kernel: [  301.622131] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:54:48 peter-desktop kernel: [  318.484063] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:55:48 peter-desktop kernel: [  378.484054] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:57:08 peter-desktop kernel: [  458.486058] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
Apr 19 20:58:48 peter-desktop kernel: [  558.484054] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251


and from dmesg grep bt:

> [   10.670013] bttv: driver version 0.9.18 loaded
[   10.670020] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   10.670076] bttv: Bt8xx card found (0).
[   10.670431] bttv 0000:02:0a.0: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[   10.670442] bttv0: Bt878 (rev 17) at 0000:02:0a.0, irq: 17, latency: 64, mmio: 0xec7fe000
[   10.671936] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[   10.671944] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[   10.671948] IRQ 17/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.671988] bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
[   10.673567] bttv0: tuner absent
[   10.673600] bttv0: add subdevice "dvb0"
[   10.944678] bt878: AUDIO driver version 0.0.0 loaded
[   41.184013] dvb_bt8xx: gave up waiting for init of module bt878.
[   41.184022] dvb_bt8xx: Unknown symbol bt878_num
[   71.184012] dvb_bt8xx: gave up waiting for init of module bt878.
[   71.184021] dvb_bt8xx: Unknown symbol bt878_start
[  101.184012] dvb_bt8xx: gave up waiting for init of module bt878.
[  101.184071] dvb_bt8xx: Unknown symbol bt878_stop
[  131.184013] dvb_bt8xx: gave up waiting for init of module bt878.
[  131.184072] dvb_bt8xx: Unknown symbol bt878
[  131.351332] bt878: Bt878 AUDIO function found (0).
[  131.351397] bt878 0000:02:0a.1: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[  131.351453] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[  131.351511] bt878(0): Bt878 (rev 17) at 02:0a.1, irq: 17, latency: 64, memory: 0xec7ff000
[  131.351637] IRQ 17/bt878: IRQF_DISABLED is not guaranteed on shared IRQs

---

### Post by ian dobson on 2010-04-19
Hi,

Are you sure it's an issue with the bttv chip? Looking at your logs I see quite afew "rt_ioctl_giwscan" errors thats comming from a wireless lan card based on a RALINK RT3070 chip.

In the log you also have serveral warnings about shared interrupts not being supported, maybe try swapping the order of the cards in the PC around abit so that each card has their own interrupt.

Regards
Ian Dobson

---

### Post by sqeelurgle on 2010-04-19
I have tried a lot of different locations for each of the tuner cards (and therefore the others as well).  The wireless LAN card functions, but I do have an older, slower one that I can put into the system and see if that works.

I'll try that and report back on how it goes

Thanks

---

### Post by sqeelurgle on 2010-04-20
OK, an update.  I removed the woreless card completely, and the problem was still the same.  I then removed the Twinhan tuner, and the system booted correctly about 4 or 5 times in a row - but there were lots of recording make use of 2 tuners.  I put that card back in - in several different slots just in case, and it went back to the random behaviour of sometimes booting correctly, and sometimes not.  I have also tried letting the BIOS select all the interrupts, and letting the OS do it (there is a BIOS setting for that). I still haven't replaced the wireless card back in.  There is something with that card, or it's driver. or the interaction between it and some other part of the system.  ANy ideas why it would boot correctly sometimes and not others?

Thanks

---

### Post by sqeelurgle on 2010-04-24
I think I might have worked something out, but I'm not sure what to do about it.  I completely reinstalled mythbuntu onto a new hard drive.  It booted completely fine every time, until I activated mythwelcome.  After that it has started to play up and not boot properly occassionally again.  ANy ideas what to look for or try?

Thanks

---

### Post by parsim on 2010-07-01
Did you get anywhere with this? I have a very similar issue.

Some boots are fine, others the bt878 module spends 60 seconds before "gave up waiting for init of module bttv". During this time mythbackend starts but of course can't find any tuners, which is very bad. 

If I restart mythbackend manually, all is well (since by then all modules have finished loading). Almost: the wireless card also fails with the ath5k driver reporting that a probe failed with error -110. I need to rmmod and modprobe it to get it back.

Edit: This began following an upgrade from mythbuntu 9.04 -> 10.04.

---

### Post by ian dobson on 2010-07-01
Hi parsim

It sounds alot like a race condition. Could you try blacklisting the bbtv module (so it doesn't start automatically on boot), then manually load the required modules later in the boot (/etc/rc.local maybe).

For mythtv you could add a look the the pre-start script for mythbackend that waits until the video device is available in /dev before loading the backend.

Regards
Ian Dobson

---

### Post by parsim on 2010-07-02
Thanks for the reply Ian.

I've been messing with it today and am not sure it's specific to bttv any more... when it boots badly, it seems one or more of a whole bunch of drivers don't load: not just the tuner cards but (sometimes) also the LCD screen, the network, and the remote control.

I need to do a bit more investigating.

---

### Post by ian dobson on 2010-07-02
Hi parsim,

Could it be drivers/hadware that need firmware to be loaded onto the hardware before it works?

If so then it could be a race condition that udev tries to start the device before the firmware directory is available.

Regards
Ian Dobson

---

### Post by parsim on 2010-07-03
Ok, so I see Ubuntu uses upstart now. That has definitely confused things, since services start in a slightly different order each boot.

I suspect my problem is interference between the 'bttv' (TV tuner) and 'ath5k' (wireless network) modules.

I blacklisted ath5k to prevent it from being loaded on boot, and since then, the tuners have loaded fine each time. I wrote a short script to modprobe ath5k once X starts, to enable networking without interfering with bttv.

Apparently unrelated (except for being a result of upstart rearranging things) are my problems with lircd and the lcd server occasionally not starting properly... more investigation required there.

---

### Post by parsim on 2010-07-05
> **parsim said:**
> Apparently unrelated (except for being a result of upstart rearranging things) are my problems with lircd and the lcd server occasionally not starting properly... more investigation required there.

And just for completeness: that was the result of this:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506/comments/92](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506/comments/92)

(I.e. 'runlevel' returns 'unknown', some non-upstart services not started on boot.)

---

