---
title: "KWorld 115 analog problem"
date: 2008-10-26
forum: Multimedia Software
---

### Post by Cogman on 2008-10-26
I don't know about the digital portion of my card, but I am having problems with the analog portion.

I just updated from 8.04 to the 8.10 release (I figure it should be pretty stable by now) overall, I have been very pleased with all the updates. One thing thats gone sour, though, is my TV input card. Currently, it is locked onto channel 2. It won't go anywhere else. I've tried Mplayer, TVtime, ect with no success in changing the channel.

Any hints on how to get away from the perpetual TV Guide channel? (the card was working perfectly in 8.04, I can only guess some driver update is the culprit)

---

### Post by cariboo on 2008-10-26
Have you had a look at this thread?

[http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld](http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld)

Jim

---

### Post by Cogman on 2008-10-26
Yes I have, I do actually get a channel, it just wont change at all (and it does come in clear and undistorted).

Of course, that is for getting the DVB chipset to work on the card, I am currently only interested in the analog chipset as that is all I have available (as of now).

However, for any that are skeptical.

dmesg
> [   24.206838] saa7130/34: v4l2 driver version 0.2.14 loaded
[   24.206884] saa7134 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.206894] saa7133[0]: found at 0000:05:01.0, rev: 209, irq: 17, latency: 64, mmio: 0xfebff800
[   24.206900] saa7133[0]: subsystem: 17de:7352, board: Kworld ATSC110/115 [card=90,autodetected]
[   24.206911] saa7133[0]: board init: gpio is 100
[   24.213462] end_request: I/O error, dev sr0, sector 16202968
[   24.213467] Buffer I/O error on device sr0, logical block 2025371
[   24.356026] saa7133[0]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356040] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356053] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356065] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356078] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356090] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356103] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356116] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356128] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356144] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356153] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356161] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356170] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356178] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356187] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.356195] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.408905] saa7133[0]: registered device video0 [v4l2]
[   24.408948] saa7133[0]: registered device vbi0
[   24.731493] saa7134 ALSA driver for DMA sound loaded
[   24.731519] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 17 registered as card -2

...

[   25.045088] nxt200x: NXT2004 Detected
[   25.121572] tuner-simple 0-0061: creating new instance
[   25.121576] tuner-simple 0-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   25.121579] DVB: registering new adapter (saa7133[0])
[   25.121582] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   25.129509] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   25.129512] firmware: requesting dvb-fe-nxt2004.fw
[   25.189642] nxt2004: Waiting for firmware upload(2)...
[   26.166987] lp: driver loaded but no devices found
[   26.748030] nxt2004: Firmware upload complete
...


lspci -vnn
> 05:01.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
	Subsystem: KWorld Computer Co. Ltd. Device [17de:7352]
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

ls -l /dev/dvb/adapter0
> total 0
crw-rw----+ 1 root video 212, 4 2008-10-26 10:19 demux0
crw-rw----+ 1 root video 212, 5 2008-10-26 10:19 dvr0
crw-rw----+ 1 root video 212, 3 2008-10-26 10:19 frontend0
crw-rw----+ 1 root video 212, 7 2008-10-26 10:19 net0

Hmm.. It is a weird problem to say the least.

---

### Post by Cogman on 2008-10-27
Just a small bump. Still haven't figured out the problem. I've tried changing permissions on /dev/video0, rebooting several times, and moving ntx2004.fw around a bit with no success.

Any tips would be much appreciated.

---

### Post by xfr on 2008-11-01
Same problem here...
Solved by using the old kernel (2.6.24-21-generic) on intrepid.

> **Cogman said:**
> Just a small bump. Still haven't figured out the problem. I've tried changing permissions on /dev/video0, rebooting several times, and moving ntx2004.fw around a bit with no success.

Any tips would be much appreciated.

---

### Post by mcendoo on 2008-11-03
I have the same issue with Ubuntu 8.10.  I have looked at all the threads on this issue I can find, but after much experimentation, I still cannot change channels on either the analog or digital tuners on the Kworld 115 card.  I have my setup with my original 8.04 system I have been running for the last six months in which the Kworld 115 works flawlessly, with a new disk containing a clean install of 8.10 in which I am unable to scan for the channels.

The following are extracts from the dmesg files from both systems.  I am not a novice with linux, but I don't know how to interpret these results.  It seems to me that the tuners are not being set up correctly but, what do I know :). Maybe someone else might understand what is going on.


dmesg from Ubuntu 8.04 with kernel 2.6.24-19-generic - Kworld 115 works properly

[   52.549398] Linux video capture interface: v2.00
[   52.807991] saa7130/34: v4l2 driver version 0.2.14 loaded
[   52.809563] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 17 (level, low) -> IRQ 19
[   52.809577] saa7133[0]: found at 0000:02:06.0, rev: 209, irq: 19, latency: 64, mmio: 0xf7dff800
[   52.809585] saa7133[0]: subsystem: 17de:7352, board: Kworld ATSC110/115 [card=90,autodetected]
[   52.809611] saa7133[0]: board init: gpio is 100
[   52.943053] saa7133[0]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   52.943067] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.943078] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.943089] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.943099] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.943109] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.943120] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.943130] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.219423] tuner 1-0061: chip found @ 0xc2 (saa7133[0])
[   53.219467] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   53.219471] tuner 1-0061: type set to Philips TUV1236D AT
[   53.219475] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   53.219478] tuner 1-0061: type set to Philips TUV1236D AT
[   53.221603] saa7133[0]: registered device video0 [v4l2]
[   53.221631] saa7133[0]: registered device vbi0
[   53.857631] nxt200x: NXT2004 Detected
[   54.209270] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 17
[   54.209613] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   54.214983] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   54.403414] DVB: registering new adapter (saa7133[0])
[   54.403423] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   54.408788] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   54.551176] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 19
[   55.103093] saa7134 ALSA driver for DMA sound loaded
[   55.103137] saa7133[0]/alsa: saa7133[0] at 0xf7dff800 irq 19 registered as card -2
[   57.210542] nxt2004: Waiting for firmware upload(2)...
[   58.889446] nxt2004: Firmware upload complete

dmesg from Ubuntu 8.10 wuth kernel 2.6.27-7-generic - unable to tune Kworld 115

[   14.426776] Linux video capture interface: v2.00
[   14.448866] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   14.632133] saa7130/34: v4l2 driver version 0.2.14 loaded
[   14.634465] saa7134 0000:02:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.634478] saa7133[0]: found at 0000:02:06.0, rev: 209, irq: 17, latency: 64, mmio: 0xf7dff800
[   14.634488] saa7133[0]: subsystem: 17de:7352, board: Kworld ATSC110/115 [card=90,autodetected]
[   14.634510] saa7133[0]: board init: gpio is 100
[   14.799187] saa7133[0]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799205] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799219] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799233] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799246] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799260] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799274] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799287] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799301] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799315] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799328] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799342] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799356] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799369] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799383] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.799397] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.875975] saa7133[0]: registered device video0 [v4l2]
[   14.876310] saa7133[0]: registered device vbi0
[   15.108528] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.129145] saa7134 ALSA driver for DMA sound loaded
[   15.129191] saa7133[0]/alsa: saa7133[0] at 0xf7dff800 irq 17 registered as card -2
[   15.180086] nxt200x: NXT2004 Detected
[   15.240055] tuner-simple 1-0061: creating new instance
[   15.240062] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   15.240069] DVB: registering new adapter (saa7133[0])
[   15.240076] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   15.248050] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   15.248059] firmware: requesting dvb-fe-nxt2004.fw
[   18.246373] nxt2004: Waiting for firmware upload(2)...
[   20.034916] lp: driver loaded but no devices found
[   21.269253] Adding 4546352k swap on /dev/sda5.  Priority:-1 extents:1 across:4546352k
[   21.416074] nxt2004: Firmware upload complete

---

### Post by Cogman on 2008-11-06
Well, it is definitely a new bug introduced by the new kernel. What is sad is the new kernel fixes many of the sound problems I was having with the Asus P5Q-E board. :( humm. So what next?

---

### Post by mcendoo on 2008-11-07
I now have the Kworld 115 working in my Ubuntu 8.10 box.  It appears, from what I have found in the V4L community, that changes made to the V4L drivers resulted in timing issues with loading the tuner modules.  The solution involves downloading the V4L source code, applying a patch, recompiling and installing the new drivers, and then loading the tuner modules on each restart (which can be automated).  It is not trivial but not that difficult, even I can do it :) There is a warning that the patch might break other tuner cards that are also in the box as it has not been extensively tested.  If anyone wants to do this, I will write up what I did when a get a little time, just post a request!

---

### Post by Cogman on 2008-11-11
I would be very appreciative if you would do this.  Thanks for the research into the problem!

---

### Post by mcendoo on 2008-11-12
The procedure I followed is based on information I found in the video4linux-list archives ([https://www.redhat.com/mailman/private/video4linux-list/](https://www.redhat.com/mailman/private/video4linux-list/)) of June 2008, and a thread in the AVS forums at [http://www.avsforum.com/avs-vb/showthread.php?t=1050693](http://www.avsforum.com/avs-vb/showthread.php?t=1050693). The video4linux list requires registration, but really does not provide any information germane to getting the card working that is not in the AVS forum thread.

Notes:
1. The procedure I followed resulted in the analog portion of the KWorld 115 working.  I have not yet tried to get the digital portion working.
2. There are warnings on the list that following this procedure might adversly affect other tv cards in the computer.
3. There are comments on the lists about the RF inputs reversing. I cannot tell if this happened in my case, as I have cable feeding both inputs.
4. The packages required to build packages needs to be installed.  I think the only ones I had to install were build-essental and the g++ compiler.

Procedure:

Download the V4L-dvb source from [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb). The latest version is at the top left hand of the page, and can be downloaded by clicking the bz2 or gz links on the second line.
Download the patch from [http://linuxtv.org/~mkrufky/fix-broken-atsc110-analog.patch](http://linuxtv.org/~mkrufky/fix-broken-atsc110-analog.patch)
Extract the V4L-dvb source bz2 or gz file. 
Copy the patch into the folder containing the extracted V4L-dvb source.
Open a command line in the folder containing the extracted V4L-dvb source.
Apply the patch using the command "patch -p1 < fix-broken-atsc110-analog.patch" in the terminal window (without the quotes :))
Type the command "make"
The compilation took about 10 minutes on my 2.4MHz Celeron.  I saw a number of warnings during the process, but the process completed without any errors.
Type the command "sudo make install"

At this point the AVS forum said to use the following commands:

make unload
modprobe saa7134-dvb
modprobe -r tuner
modprobe tuner

When I tried this I got errors about missing symbols. I got it working by rebooting my computer.  I then used the following command from a terminal window

sudo modprobe -r tuner
sudo modprobe tuner

And Voila! I opened tvtime and was able to scan for and select channels.

The last two commands have to be issued every time the computer is booted.  I put the lines 

modprobe -r tuner
modprobe tuner

in the /etc/rc.local file (just above exit0), which automatically executes them on each restart.

Since the V4L-dvb drivers are part of the kernel package, this procedure will have to be followed every time the kernel is updated, at least until the underlying timing issue is resolved.

Please post success or failure!  If you have any problems post them and I will try to assist.

Good luck!

---

