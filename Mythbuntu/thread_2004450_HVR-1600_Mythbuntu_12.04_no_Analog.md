---
title: "HVR-1600 Mythbuntu 12.04 no Analog"
date: 2012-06-15
forum: Mythbuntu
---

### Post by houndnews on 2012-06-15
The digital side of my hvr-1600 works, can find and receive cable,  some but not all, unencrypted channels but the analog side does not seem to be detected.  The digital side is detected as an Samsung S5H1409 QAM/ Subtype ATSC at /dev/dvb/adapter0/frontend0 DVB DTV Capture Card (v3.x).  Under Mythbuntu 10.4, going from memory, the analog side is detected initially as a V4L at /dev/video0 hvr-1600 then you have to switch to IVTV to find channels but the digital side does not work.

So 12.04 no analog cable, 10.04 no digital cable.  Any recommendations for getting analog working in 12.04, either Mythbuntu or Ubuntu.  Analog is still available in my area on cable, the card works okay under windows 7 same hardware, dual boot system.  Many posts about the hvr-1600 seem dated so looking for something that works with 12.04.

---

### Post by matt06 on 2012-06-15
Is your card being detected properly (at boot, what does 'dmesg' say)?  Have you tried loading the latest V4L-DVB drivers?

I'm also wondering what your issue was with digital on 10.04 and the HVR-1600?

---

### Post by nickrout on 2012-06-16
What driver does the digital side use? Is the driver loaded? What does dmesg say? The wiki page says firmware is needed for analogue, what does dmesg say about the firmware? Is the linux-firmware-nonfree package installed? Is /dev/video0 present?

In other words what troubleshooting have you actually done?

---

### Post by klc5555 on 2012-06-16
The problem with Ubuntu 10.04 and the 1600's digital was that the version of the cx18 driver included in 10.04 predated most of the solution of the amplification issues with digital. One generally got much better results on 10.04 machines by compiling and installing later source for the cx18 module, to the extent that one would sometimes have to use an attenuator to keep very strong digital channels from swamping the tuner and preventing channel locks.

I have four older units of these cards (various models including the two variants that won't do QAM on Windows) currently doing QAM and analog on kernels from 2.39.4 to 3.3.4 without any special modifications. I would find it implausible then that an older-version 1600 analog tuner that was detected and ran on unmodified plain-vanilla 10.04 would now be undetected on current kernels.

So, seconding what nickrout said, what does the output of lspci and dmesg | grep cx18 say about the detection of the analog tuner and the loading of the cx18 module?

Are the conexant firmware files necessary for analog present under /lib/firmware ( v4l-cx23418-apu.fw, v4l-cx23418-cpu.fw, and v4l-cx23418-dig.fw) Did they load at boot? If missing, these files are to be found in the package "linux-firmware".

---

### Post by houndnews on 2012-06-16
Have been working on this for some time but no luck.

dmesg | grep cx18
[   15.323458] cx18:  Start initialization, version 1.5.1
[   15.323555] cx18-0: Initializing card 0
[   15.323558] cx18-0: Autodetected Hauppauge card
[   15.323593] cx18 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.323601] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   15.327473] cx18-0: cx23418 revision 01010000 (B)
[   15.562931] cx18-0: Autodetected Hauppauge HVR-1600
[   15.562932] cx18-0: Simultaneous Digital and Analog TV capture supported
[   15.682670] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   15.707283] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   15.707286] DVB: registering new adapter (cx18)
[   15.898194] cx18-0: DVB Frontend registered
[   15.898196] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   15.898236] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   15.898267] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   15.898354] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   15.898356] cx18-0: Initialized card: Hauppauge HVR-1600
[   15.898521] cx18:  End initialization
[   15.901171] cx18-alsa: module loading...
[   16.063397] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   16.242485] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   16.248834] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   17.201330] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   17.231234] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Firmware is in /lib/firmware ( v4l-cx23418-apu.fw, v4l-cx23418-cpu.fw, and v4l-cx23418-dig.fw).  Rebuilt v4l-dvb from instructions here [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers).  Old firmware filesizes same size as new so no luck there.  

lsmod | grep cx
cx18_alsa              13730  1 
cx18                  127896  2 cx18_alsa
dvb_core              110010  1 cx18
cx2341x                28283  1 cx18
i2c_algo_bit           13423  1 cx18
videobuf_vmalloc       13589  1 cx18
videobuf_core          26022  2 cx18,videobuf_vmalloc
tveeprom               21249  1 cx18
v4l2_common            16454  4 cs5345,tuner,cx18,cx2341x
videodev              124809  5 cs5345,tuner,cx18,cx2341x,v4l2_common
snd_pcm                97188  3 cx18_alsa,snd_hda_intel,snd_hda_codec
snd                    78855  18 cx18_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

So cx modules appear to be loaded.  Reran backend and no new card is detected Analog V4L or MPEG, just the Samsung ATSC.  I remember the analog side ran in 10.04 under IVTV but that option no longer available, something missing there?

PhenomII x2, 4GB ram, 7200rpm 1TB drive, Gigabyte MA770T-UD3P.

---

### Post by matt06 on 2012-06-16
Well, nothing jumps out at me that says something is wrong.  It appears that the card is being loaded properly, at least as far as the kernel is concerned.

I'm not familiar with configuring the card or the status of using the ivtv analog selection in myth 0.25, hopefully someone running that version can provide some insight.

---

### Post by nickrout on 2012-06-16
> **houndnews said:**
> Have been working on this for some time but no luck.

dmesg | grep cx18
[   15.323458] cx18:  Start initialization, version 1.5.1
[   15.323555] cx18-0: Initializing card 0
[   15.323558] cx18-0: Autodetected Hauppauge card
[   15.323593] cx18 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.323601] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   15.327473] cx18-0: cx23418 revision 01010000 (B)
[   15.562931] cx18-0: Autodetected Hauppauge HVR-1600
[   15.562932] cx18-0: Simultaneous Digital and Analog TV capture supported
[   15.682670] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   15.707283] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   15.707286] DVB: registering new adapter (cx18)
[   15.898194] cx18-0: DVB Frontend registered
[   15.898196] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   15.898236] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   15.898267] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   15.898354] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   15.898356] cx18-0: Initialized card: Hauppauge HVR-1600
[   15.898521] cx18:  End initialization
[   15.901171] cx18-alsa: module loading...
[   16.063397] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   16.242485] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   16.248834] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   17.201330] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   17.231234] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Firmware is in /lib/firmware ( v4l-cx23418-apu.fw, v4l-cx23418-cpu.fw, and v4l-cx23418-dig.fw).  Rebuilt v4l-dvb from instructions here [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers).  Old firmware filesizes same size as new so no luck there.  

lsmod | grep cx
cx18_alsa              13730  1 
cx18                  127896  2 cx18_alsa
dvb_core              110010  1 cx18
cx2341x                28283  1 cx18
i2c_algo_bit           13423  1 cx18
videobuf_vmalloc       13589  1 cx18
videobuf_core          26022  2 cx18,videobuf_vmalloc
tveeprom               21249  1 cx18
v4l2_common            16454  4 cs5345,tuner,cx18,cx2341x
videodev              124809  5 cs5345,tuner,cx18,cx2341x,v4l2_common
snd_pcm                97188  3 cx18_alsa,snd_hda_intel,snd_hda_codec
snd                    78855  18 cx18_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

So cx modules appear to be loaded.  Reran backend and no new card is detected Analog V4L or MPEG, just the Samsung ATSC.  I remember the analog side ran in 10.04 under IVTV but that option no longer available, something missing there?

PhenomII x2, 4GB ram, 7200rpm 1TB drive, Gigabyte MA770T-UD3P.

It's an mpeg card, given that ivtv is now not the ONLY driver for hardware mpeg encoders the name has been changed to be more logical.

---

### Post by klc5555 on 2012-06-16
Well, certainly the cx18 module appears to be loading correctly and registers a device node at /dev/video0 So the issue would appear to be a pure mythtv issue rather than anything with the OS, drivers, and firmware.

By "reran backend" you meant "reran the backend setup" from the control centre or sudo mythtv-setup to add a "new capture card"? And no /dev/videoX's appeared at all in the "New Capture Card" form to scroll through, not even odd ones like /dev/video25 or /dev/video33, which sometimes udev likes to move this tuner onto? If you manually type /dev/video0 into the device line of the form and indicate V4L analog (or MPEG), do you get a "failed to open" error?

---

### Post by houndnews on 2012-06-17
Reran backend setup no /dev/video0 shows up just /dev/vbi0 with no other choice being available under V4L or MPEG or MPEG-2.   All display "Failed to open".  There is, under /dev,  a video0, video24, video32, (as well as vbi0).  Typed these into V4l, MPEG, and MPEG-2 selections and still get "Failed to open".  Looking at /etc/udev/rules.d there are only 2 files, one for cd and one for net, with no mention of any tuner card.

I used Clonezilla to back up this install, was thinking of installing Mythbuntu 10.04 for comparison, maybe worthwhile?  These installs are all 64 bit.

---

### Post by klc5555 on 2012-06-17
You might do best posting a query on the Mythtv mailing list, since this at first blush appears to be a pure Mythtv issue, rather than a driver/firmware/OS issue.

But certainly, if you feel like trying a backleveled version, 10.04 with myth0.23.1 will be fine for comparision, though you'll want to compile more recent dvb driver source for better digital on the 1600. 11.10 with mythtv 024.x might be a better choice still.

---

### Post by nickrout on 2012-06-17
> **houndnews said:**
> Reran backend setup no /dev/video0 shows up just /dev/vbi0 with no other choice being available under V4L or MPEG or MPEG-2.   All display "Failed to open".  There is, under /dev,  a video0, video24, video32, (as well as vbi0).  Typed these into V4l, MPEG, and MPEG-2 selections and still get "Failed to open".  Looking at /etc/udev/rules.d there are only 2 files, one for cd and one for net, with no mention of any tuner card.

I used Clonezilla to back up this install, was thinking of installing Mythbuntu 10.04 for comparison, maybe worthwhile?  These installs are all 64 bit.

/dev/video0 is the one you want. What are the permissions on that file?

---

### Post by houndnews on 2012-06-17
For /dev/video0 root and video have read and write permissions, others have none.

---

### Post by nickrout on 2012-06-17
> **houndnews said:**
> For /dev/video0 root and video have read and write permissions, others have none.

well the only reason it wouldn't come up in mythtv-setup as a mpeg2 encoder is if you already have it defined as a cpature card.

Do you have any cards defined at present? The output of the following sql statement would be helpful:

```
select cardid,videodevice,cardtype from capturecard;
```

---

### Post by houndnews on 2012-06-17
If I got into mysql correctly -

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+

mysql> use information_schema;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select cardid,videodevice,cardtype from capturecard;
ERROR 1109 (42S02): Unknown table 'capturecard' in information_schema

So no capture card defined if I'm reading this correctly and am in the correct database.

---

### Post by nickrout on 2012-06-17
> **houndnews said:**
> If I got into mysql correctly -

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+

mysql> use information_schema;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select cardid,videodevice,cardtype from capturecard;
ERROR 1109 (42S02): Unknown table 'capturecard' in information_schema

So no capture card defined if I'm reading this correctly and am in the correct database.

Is that on the backend? There should be a table mythconverg. 

Are you connecting as user mythtv with the password that is set in /home/mythtv/.mythtv/mysql.txt ?

---

### Post by jmore9 on 2012-06-18
I use a vesion the same card 1600 and i had to use the following from the linuxtv.org site, for analog.


Firmware

The firmware can be obtained from [here]. It is required only for the analog (V4L) functionality of the device. 

Everything else but that worked right from the intall nothing to install.

Maybe this will help maybe not.

---

### Post by houndnews on 2012-06-19
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mythconverg        |
| test               |
+--------------------+
3 rows in set (0.00 sec)

mysql> use mythconverg;
Database changed
mysql> select cardid,videodevice,cardtype from capturecard;
+--------+-----------------------------+----------+
| cardid | videodevice                 | cardtype |
+--------+-----------------------------+----------+
|      1 | /dev/dvb/adapter0/frontend0 | DVB      |
|      2 | /dev/dvb/adapter0/frontend0 | DVB      |
+--------+-----------------------------+----------+
2 rows in set (0.00 sec)

mysql>

---

### Post by houndnews on 2012-06-19
Think your links are: 
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)
[http://www.ivtvdriver.org/index.php/Cx18#Firmware](http://www.ivtvdriver.org/index.php/Cx18#Firmware)
Already been tried, no luck.  Built firmware has same filesizes as three originals supplied with distro.  You are using 12.04?

---

### Post by hacjr on 2012-06-25
Any update on this issue?  Just did an upgrade to my system and ran   into the exact same thing.  Please help.

---

### Post by houndnews on 2012-06-25
Reinstalled MB 10.04 and got analog back, after I remembered to switch from v4l to ivtv, but digital side is detected but does not work.  Tried a new thread here [http://www.mythtvtalk.com/hvr-1600-mythbuntu-12-04-no-analog-15674/](http://www.mythtvtalk.com/hvr-1600-mythbuntu-12-04-no-analog-15674/)
Have tried moving hvr-1600 to different pci slot and underclocking the mobo down to 2.4 Ghz from 3.5 but no luck.  Guessing something got lost in transition from legacy v4l to v4l2?

---

### Post by klc5555 on 2012-06-26
The cx18 driver included with 10.04 was quite old. Though the analog bugs had largely been worked out (the cx18 included in 9.04 didn't work at all, for example, because of a race condition), the amplification issues with digital had not been solved yet by the time 10.04 came out. 

With the cx18 driver in 10.04 you'll likely need either use a small signal amp to get satisfactory digital (or even signal locks). Or, you can compile and install a somewhat newer version of the v4l-dvb drivers than were included in 10.04. The final archived version in the old Mercurial archive is good enough --I used it on 9.04 for over a year for digital without needing amplification on a 1600 card. [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/) Or later source can be gotten from git via [http://linuxtv.org/downloads/](http://linuxtv.org/downloads/)

Can't address the 12.04 issue; I have no idea why Mythtv 0.25 backend setup fails to recognize a defined device node (/dev/video0) supplied by the OS. Perhaps yet another reason to remain for the time being on 0.24.3, where all my hardware  works (including my various 1600 cards). Hopefully the mythtv people over at the Gossamer Threads list will help you find an answer.

---

### Post by klc5555 on 2012-06-29
Well, at least I seem to have been able to recreate your Hauppauge symptoms and work around them.

It occurred to me that all my Hauppauge 1600s on Mythtv 0.24.3 were on systems where mythtv had been upgraded from 0.22 to 0.24. None were clean installs.

I have an 8-year-old AMD box that I use as a test bed. 4 years ago it used to run a Hauppauge 1600 on Mythtv 0.20.2. I put the same old Hauppauge 1600 back in the machine, slapped a new install of a stripped-down Slackware on it with kernel 3.2.21 and Mythtv 0.24.0, and attempted to run mythtv-setup. Though /dev/video0 was registered when the cx18 module loaded at boot, Mythtv 0.24.0 couldn't detect the device node in the Capture card setup and presented no analog options whatever, V4l or otherwise in Capture Card setup. Digital could be set up normally. 

These seemed to be the same symptoms you were experiencing with Mythbuntu 12.04/Mythtv 0.25.

I then replaced Mythtv 0.24 with Mythtv 0.22 and another clean mythconverg database. No aspect of the installed operating system was altered other than mythtv version. Now /dev/video0 was recognized perfectly by the 0.22 version of mythtv-setup Both analog and digital could be configured on the 1600 card, and both received liveTV signals as expected through mythfrontend.

For the final stage of the test, this functioning Mythtv 0.22 installation was package-upgraded back to 0.24.3, with no other aspect of the OS altered. Once mythbackend upgraded the older schema from the 0.22 mythconverg to the current level, the Hauppauge 1600 continued to function on both digital and analog on the test 0.24.3 installation.

So I conclude from this that the problem with the "invisible /dev/vide0" device node for the Hauppauge 1600, whatever its cause, seems to be a pure Mythtv issue, rather than OS or hardware related. It seems to exist already in 0.24 and by your experience persists in 0.25. The workaround I succeeded with was in configuring this card correctly, digital and analog, in a version of mythtv earlier than 0.24 (in this case 0.22), and then package-upgrading mythtv to 0.24.3, allowing mythbackend to upgrade the database schema the first time it ran.

For you, the workaround would appear to start with configuring the analog side of the 1600 correctly in 10.04 running Mythtv 0.23.0, as you have done, then use the repos to move the Mythtv on this machine to 0.24.x. Then, once you've confirmed your analog still functions in the Mythtv 0.24 environment, proceed to do an upgrade to 12.04/Mythtv 0.25. Don't do a fresh install. Assuming the analog half of the 1600 still functions as it should after the upgrade, you can go ahead and configure the digital to go along with it.

Or alternatively I suppose that you could configure the analog in 10.04, back up mythconverg, do a clean install of 12.04, restore to it your mythconverg from 10.04, and run mythbackend to upgrade the schema to the current level. Then configure digital. Either way, I believe you should end up with a current mythtv version where your Hauppauge 1600 does both analog and digital properly.

---

### Post by matt06 on 2012-06-29
Nice work klc!  I'm assuming if one follows this route of configuring the card in a previous version of Myth and then upgrading to a newer version, then you *must* leave the card installed as-is and would not be able to remove or reconfigure it at all?

I've been known to remove one of my cards to do some testing on another system and then reinstall it, so I'm definitely glad I haven't moved on to 0.25 (yet).  This must be an oversight by the MythTV devs, hopefully it gets patched at some point.

---

### Post by klc5555 on 2012-06-30
> **matt06 said:**
> Nice work klc!  I'm assuming if one follows this route of configuring the card in a previous version of Myth and then upgrading to a newer version, then you *must* leave the card installed as-is and would not be able to remove or reconfigure it at all?

I've been known to remove one of my cards to do some testing on another system and then reinstall it, so I'm definitely glad I haven't moved on to 0.25 (yet).  This must be an oversight by the MythTV devs, hopefully it gets patched at some point.

I've reconfigured a 1600's analog in situ on Myth 0.24 without ever noticing a bug, so I'm guessing that once the entries for the tuner at /dev/video0 have been made successfully in mythconverg, you can modify them as you would normally expect to do with any card.

However, I've never *deleted* a Hauppauge 1600 analog tuner from 0.24's backend setup en route to physically removing the card, but later returning the card to the machine with the same 0.24 installation and attempting to add the card again to the backend with "add new card" in the backend setup. So I simply don't know what will happen in that case.

---

### Post by houndnews on 2012-06-30
Thanks for the big effort KLC,  will give it a try shortly, as soon as I iron out a few other issues with my MB 12.04 Firewire setup.  Got a Motorola dct 6412 attached to a local 
BE accessed by a remote notebook FE working, just have to do a few more tweaks.

---

### Post by houndnews on 2012-07-08
Thanks klc5555.  After a clean install and update of MB 10.04, I took your 2nd suggestion and backed up mythconverg after it was set up.  I used mythconverg_backup.pl per these instructions
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Backup](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Backup).  

After storing the backup in a safe location I did a clean install of MB 12.04 and replaced mythconverg via mythconverg_restore.pl --drop_database --create_database --filename mythconverg...  After stopping the BE the schema wanted to update so I did that.  I ran the FE, which also wanted a schema update, and analog NTSC was working :)  I then reran the BE which saw the ATSC side of the card and found channels when I ran the channel scan.

Unfortunately,  although the analog is now working I cannot select the discovered digital channels.  The analog side is tuner1 and I can't seem to get it to change over to the other side of the tuner.  But basically your suggestion was a success.  I'll mark this post as solved by workaround.  Thanks again.

PS - Got my other BE machine hooked up to a DCT 6412 via firewire up and running and can view all channels analog/digital/SD/HD via remote notebook FE over wifi, really neat.

---

### Post by klc5555 on 2012-07-08
Glad you've got analog now in 12.04 :D

But it sounds a little like you've been trying to use the same video source for both analog and digital, which wouldn't work. (I couldn't quite parse the comment about "getting it to change over to the other side of the tuner".) The 1600 is essentially two completely separate tuners on one card and can record from both tuners simultaneously. These tuners would be set up completely independently with a 2-way splitter and coax connected to both ports, and would require 2 video sources: one video source scanned and populated with just analog channels and bound to the analog tuner1 at /dev/video0, and a second video source scanned and populated with just digital channels and bound to the digital tuner at /dev/dvb/adapter0/frontend0

---

### Post by houndnews on 2012-07-08
Got both NTSC and ATSC working with my hvr-1600 in MB 12.04.  Started from scratch, saving mythconverg from MB 10.04.  After replacing mythconverg in MB 12.04, made sure I had two video sources defined, one for analog and one for digital.  Everything now working, so far:)

---

