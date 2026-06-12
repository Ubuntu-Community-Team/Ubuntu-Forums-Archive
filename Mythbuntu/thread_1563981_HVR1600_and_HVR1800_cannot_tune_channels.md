---
title: "HVR1600 and HVR1800 cannot tune channels"
date: 2010-08-29
forum: Mythbuntu
---

### Post by MALDATA on 2010-08-29
I am at the end of my rope. I've tried Fedora, MythDora, Gentoo, Ubuntu, and now MythBuntu. I've tried three different machines with completely different hardware. I've tried both the HVR1600 and the HVR1800.

In every case, I get the same result. All of the hardware loads fine (according to dmesg and the myth setup), but the scan doesn't show any channels coming from my ATSC antenna. I KNOW that there are channels there because if I hook it directly to my TV I get several channels with good reception.

I have no idea what to do. Everything I see in the forums is from several years ago and has more to do with just getting the hardware installed. That doesn't seem to be a problem any more. All of the hardware APPEARS to work out-of-the-box.

My info for the current setup is:

MythBuntu 10.04
HVR1600

Output of dmesg | grep cx18:
```

[   23.618869] cx18:  Start initialization, version 1.2.0
[   23.618937] cx18-0: Initializing card 0
[   23.618944] cx18-0: Autodetected Hauppauge card
[   23.642614] cx18 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.652584] cx18-0: cx23418 revision 01010000 (B)
[   23.998237] cx18-0: Autodetected Hauppauge HVR-1600
[   23.998242] cx18-0: Simultaneous Digital and Analog TV capture supported
[   24.136984] IRQ 17/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.373069] tuner 3-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   24.458977] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   24.472067] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   24.499509] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   24.499516] DVB: registering new adapter (cx18)
[   24.654296] cx18-0: DVB Frontend registered
[   24.654300] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   24.654355] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   24.654401] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   24.654447] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   24.654493] cx18-0: Registered device radio0 for encoder radio
[   24.654498] cx18-0: Initialized card: Hauppauge HVR-1600
[   24.654531] cx18:  End initialization
[   24.677230] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-cpu.fw
[   24.787654] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   24.885523] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-apu.fw
[   25.003528] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   25.010191] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   25.262451] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-cpu.fw
[   25.399810] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-apu.fw
[   25.722313] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-dig.fw
[   25.920428] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   25.939417] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

```

Output of lspci -v
```

02:02.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
	Subsystem: Hauppauge computer works Inc. Device 7400
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: cx18
	Kernel modules: cx18

```

Output of dmesg | grep tuner:
```

[   13.432727] tveeprom 2-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   14.507821] tuner 3-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   14.850268] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   15.117393] tuner-simple 3-0061: creating new instance
[   15.117399] tuner-simple 3-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))

```

Output of lsmod:
```

Module                  Size  Used by
snd_intel8x0           25588  0 
snd_ac97_codec        100646  1 snd_intel8x0
mxl5005s               36463  1 
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
s5h1409                 8258  1 
tuner_simple           13577  1 
tuner_types            14233  1 tuner_simple
cs5345                  2546  1 
tda9887                 9589  1 
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
tda8290                12092  0 
snd_seq_dummy           1338  0 
tuner                  20412  2 
fbcon                  35102  73 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
vga16fb                11385  0 
nfsd                  238967  13 
exportfs                3437  1 nfsd
nfs                   264813  0 
lockd                  64849  2 nfsd,nfs
nfs_acl                 2245  2 nfsd,nfs
snd_rawmidi            19056  1 snd_seq_midi
vgastate                8961  1 vga16fb
cx18                  104801  1 
dvb_core               86142  1 cx18
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
cx2341x                12469  1 cx18
v4l2_common            15431  4 cs5345,tuner,cx18,cx2341x
auth_rpcgss            33735  2 nfsd,nfs
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videodev               34361  4 cs5345,tuner,cx18,v4l2_common
snd_timer              19098  2 snd_pcm,snd_seq
v4l1_compat            13251  1 videodev
ir_common              38875  1 cx18
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tveeprom               11102  1 cx18
radeon                674824  3 
i82875p_edac            3314  0 
ttm                    49943  1 radeon
sunrpc                193085  12 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
edac_core              37331  3 i82875p_edac
drm_kms_helper         29297  1 radeon
intel_agp              24119  1 
snd                    54148  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
drm                   162409  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  2 cx18,radeon
agpgart                31724  3 ttm,intel_agp,drm
shpchp                 28820  0 
dell_wmi                1793  0 
ppdev                   5259  0 
dcdbas                  5422  0 
psmouse                63245  0 
parport_pc             25962  1 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
e100                   28211  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
floppy                 53016  0 
mii                     4381  1 e100

```

Please put me out of my misery.

Thanks.

---

### Post by JMcFly on 2010-08-30
Scan function hasn't worked since at least 9.04 IIRC, you need to either assign the channels manually in the back end ([www.antennaweb.org](www.antennaweb.org) to find out which ones you should have given your antenna and location) and then go into system setup on Mythweb to link each callsign to an XML tag from SchedulesDirect (hover over each channel in your line-up for a pop-up box to give the XML tag number, should be five digits).  Or, you can just hit the 'fetch channels from listing source' button in the backend and it should (should...) populate them for you.

---

### Post by klc5555 on 2010-08-30
I use 3 of these HVR-1600 cards, one on a Mythbuntu 9.04 machine, and two more on a Slackware 13.1 box running Mythtv 0.21. There are a few possible issues that may have snagged you.

First, the simplest: cabling must be done specifically to the ATSC port of the card for digital, and scanning should be done on 8-VSB (sorry, have to mention it --I think about 80% of all computer hardware issues revolve around cabling).

Second, the cx18 driver often does not load correctly at boot, although it appears to have done so. With this driver condition, the card may not tune, may tune but have no picture, or may have picture but display missing or degraded audio. The cx18 module has to be reloaded using "sudo rmmod cx18" and "sudo modprobe cx18" On current kernels with the latest version of the driver, you may have to unload cx18_alsa _first_, before unloading the main cx18 driver. 

Third, there are many versions of the 1600 using different tuners; the cx18 driver may load, but may fail to correctly identify the card's actual tuner. When the tuner is correctly identified, its tuner number will have to be passed to the cx18 module as an option when the cx18 module is loaded. Iglenn has composed a script to sequentially test a 1600 card against the full range of possible tuner parameters. A link to it is found at the end of this thread: [http://ohioloco.ubuntuforums.org/showthread.php?t=1498620&page=2&highlight=hauppauge+1600+script+tuner](http://ohioloco.ubuntuforums.org/showthread.php?t=1498620&page=2&highlight=hauppauge+1600+script+tuner)

Fourth, the Linux cx18 driver for the Hauppauge 1600 has long had odd issues, including stuttering playback and significant digital signal strength requirements. These issues have been and continue to be addressed, and the situation is vastly improved in current patched versions of the driver, which were supposed to be incorporated into the kernel tree along about kernel 2.6.33 or so. However, Ubuntu 10.04 uses the 2.6.32 series (and Slack doesn't even bother including the v4l-dvb modules at all, of course ...) So as a practical matter, I've always had to compile my own drivers to use this card successfully --you likely will need to also. The daily driver source snapshot is available at [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) In a standard Mythbuntu install you'll likely have to install the kernel headers, kernel source, and gcc compiler to compile/install the v4l-dvb source.

Those are the possible issues that come immediately to mind.

---

### Post by MALDATA on 2010-08-30
> Scan function hasn't worked since at least 9.04 IIRC, you need to either assign the channels manually in the back end ([www.antennaweb.org](www.antennaweb.org) to find out which ones you should have given your antenna and location) and then go into system setup on Mythweb to link each callsign to an XML tag from SchedulesDirect (hover over each channel in your line-up for a pop-up box to give the XML tag number, should be five digits). Or, you can just hit the 'fetch channels from listing source' button in the backend and it should (should...) populate them for you.

JMcFly: Thanks for the ideas... I will try this out tonight. You mention that scanning hasn't worked since 9.04... do you think that's a universal state-of-the-driver issue? As I said I've tried several distros with no success, but they've all been recent and up-to-date. I'm hoping that this means that all of them are plagued by the same problem.

Now klc5555:
> First, the simplest: cabling must be done specifically to the ATSC port of the card for digital, and scanning should be done on 8-VSB (sorry, have to mention it --I think about 80% of all computer hardware issues revolve around cabling).

No worries, I always appreciate someone checking on the small stuff. I am certain that I am using the ATSC port if for no other reason than that I've tried ALL the ports about 5 times... Just to be sure, it's the one that says "ANT IN," correct?

> Second, the cx18 driver often does not load correctly at boot, although it appears to have done so.

I tried unloading it, but I didn't know what the dependencies are. Apparently cx18_alsa. Thanks, I will try that.

> Third, there are many versions of the 1600 using different tuners; the cx18 driver may load, but may fail to correctly identify the card's actual tuner. When the tuner is correctly identified, its tuner number will have to be passed to the cx18 module as an option when the cx18 module is loaded.

I thought about this, but I couldn't find a list of tuner types to try. I will try that script and just brute-force it. Thanks for the link.

> Fourth, the Linux cx18 driver for the Hauppauge 1600 has long had odd issues, including stuttering playback and significant digital signal strength requirements. These issues have been and continue to be addressed, and the situation is vastly improved in current patched versions of the driver, which were supposed to be incorporated into the kernel tree along about kernel 2.6.33 or so.

I tried that when I had Gentoo installed, but it didn't make a difference. I guess I figured I'd cross that bridge when I got to it... better to get it working poorly first. But I will start with the most recent drivers now. Is there a difference in the versions of the firmware that has to go with it?

Thanks for the help! I've sunk a lot of time into this already, and I refuse to let this thing beat me. Do me a favor and check in again later, I'll try these things tonight and report back on any success or failure. If I'm able to get this thing going I will build several statues in your honor. Let me know if you have requests (e.g., riding a horse, wearing a toga, etc.)

---

### Post by klc5555 on 2010-08-30
> **MALDATA said:**
> 

No worries, I always appreciate someone checking on the small stuff. I am certain that I am using the ATSC port if for no other reason than that I've tried ALL the ports about 5 times... Just to be sure, it's the one that says "ANT IN," correct?



I tried unloading it, but I didn't know what the dependencies are. Apparently cx18_alsa. Thanks, I will try that.



I thought about this, but I couldn't find a list of tuner types to try. I will try that script and just brute-force it. Thanks for the link.



I tried that when I had Gentoo installed, but it didn't make a difference. I guess I figured I'd cross that bridge when I got to it... better to get it working poorly first. But I will start with the most recent drivers now. Is there a difference in the versions of the firmware that has to go with it?

Thanks for the help! I've sunk a lot of time into this already, and I refuse to let this thing beat me. Do me a favor and check in again later, I'll try these things tonight and report back on any success or failure. If I'm able to get this thing going I will build several statues in your honor. Let me know if you have requests (e.g., riding a horse, wearing a toga, etc.)

Digital terrestrial and QAM go into the shorter stubbier coax connection on the 1178, 1181 and 1199 models that have only two coax ports. The longer one (whatever it's labelled) is for analog. In the 1101 and similar, there is also a 3rd coax in for FM. "TV-in" on the two-port models appears to be the analog port. The "2 coax connector" boards have a connection picture here: [http://hauppauge.lightpath.net/manuals/qi-hvr-1600.pdf](http://hauppauge.lightpath.net/manuals/qi-hvr-1600.pdf)
The layout for the 3-coax 1600s are on page two of this manual here: [http://hauppauge.lightpath.net/manuals/qi-mce_kit_1600_1800.pdf](http://hauppauge.lightpath.net/manuals/qi-mce_kit_1600_1800.pdf) Might want to double check.

Two months ago, when I compiled the current v4l-dvb driver snapshot after replacing an old pvr-150 with a 1600 on my Mythbuntu 9.04 box, I didn't specifically touch the firware, nor did I on the other machine when driver compiling after moving from a 2.6.27 kernel to 2.6.33.4, so I imagine you'll be fine with your current firmware.

Good luck!

---

### Post by JMcFly on 2010-08-30
The scan feature was disabled for all cards because it was buggy/unreliable from what I remember.

---

### Post by MALDATA on 2010-08-30
Nothing but failure.

> Scan function hasn't worked since at least 9.04 IIRC, you need to either assign the channels manually in the back end ([www.antennaweb.org](www.antennaweb.org)  to find out which ones you should have given your antenna and location) and then go into system setup on Mythweb to link each callsign to an XML tag from SchedulesDirect (hover over each channel in your line-up for a pop-up box to give the XML tag number, should be five digits). Or, you can just hit the 'fetch channels from listing source' button in the backend and it should (should...) populate them for you.

Seems like I can't do this until I pay for a subscription to SchedulesDirect, and I'm not going to do that unless I know I can get this working. Is there any way to do this completely manually?

> First, the simplest: cabling must be done specifically to the ATSC port of the card for digital

I've got it on the ATSC input and I'm not moving it anymore.

> Second, the cx18 driver often does not load correctly at boot, although it appears to have done so. With this driver condition, the card may not tune, may tune but have no picture, or may have picture but display missing or degraded audio. The cx18 module has to be reloaded using "sudo rmmod cx18" and "sudo modprobe cx18" On current kernels with the latest version of the driver, you may have to unload cx18_alsa _first_, before unloading the main cx18 driver.

After installing the trunk dvb drivers, it still won't unload!

```
root@mythtv:~# rmmod cx18_alsa
root@mythtv:~# rmmod cx18
ERROR: Module cx18 is in use
root@mythtv:~# lsmod | grep cx18
cx18                  109824  1 
dvb_core               85978  1 cx18
cx2341x                12372  1 cx18
v4l2_common            17381  4 cs5345,tuner,cx18,cx2341x
i2c_algo_bit            5028  2 radeon,cx18
videodev               42138  4 cs5345,tuner,cx18,v4l2_common
tveeprom               11038  1 cx18
```

> Third, there are many versions of the 1600 using different tuners; the cx18 driver may load, but may fail to correctly identify the card's actual tuner. When the tuner is correctly identified, its tuner number will have to be passed to the cx18 module as an option when the cx18 module is loaded. Iglenn has composed a script to sequentially test a 1600 card against the full range of possible tuner parameters. A link to it is found at the end of this thread: [http://ohioloco.ubuntuforums.org/sho...0+script+tuner](http://ohioloco.ubuntuforums.org/sho...0+script+tuner)

I can't do this until the module unloading problem gets resolved... the script needs to unload and load the module several times.

> Fourth, the Linux cx18 driver for the Hauppauge 1600 has long had odd issues, including stuttering playback and significant digital signal strength requirements. These issues have been and continue to be addressed, and the situation is vastly improved in current patched versions of the driver

I did install the drivers successfully, but as you can see above, that didn't change anything.

Please let me know what you think I should do now, and thanks again for all the help!

---

### Post by DemonBob on 2010-08-30
> **MALDATA said:**
> Nothing but failure.



Seems like I can't do this until I pay for a subscription to SchedulesDirect, and I'm not going to do that unless I know I can get this working. Is there any way to do this completely manually?



I've got it on the ATSC input and I'm not moving it anymore.



After installing the trunk dvb drivers, it still won't unload!

```
root@mythtv:~# rmmod cx18_alsa
root@mythtv:~# rmmod cx18
ERROR: Module cx18 is in use
root@mythtv:~# lsmod | grep cx18
cx18                  109824  1 
dvb_core               85978  1 cx18
cx2341x                12372  1 cx18
v4l2_common            17381  4 cs5345,tuner,cx18,cx2341x
i2c_algo_bit            5028  2 radeon,cx18
videodev               42138  4 cs5345,tuner,cx18,v4l2_common
tveeprom               11038  1 cx18
```



I can't do this until the module unloading problem gets resolved... the script needs to unload and load the module several times.



I did install the drivers successfully, but as you can see above, that didn't change anything.

Please let me know what you think I should do now, and thanks again for all the help!

Schedule Direct offers a 7 day trial. [https://www.schedulesdirect.org/signup](https://www.schedulesdirect.org/signup)

---

### Post by JMcFly on 2010-08-31
I used SD's trial period when I set up my system, if you go more than a week without being sure of it working the two-month membership is only $5.

---

### Post by ian dobson on 2010-08-31
Hi,

Could you use w_scan to create a channels.conf that you can then use to seed the mythtv tuner/channel scanner?

Regards
Ian Dobson

---

### Post by MALDATA on 2010-08-31
> Schedule Direct offers a 7 day trial. [https://www.schedulesdirect.org/signup](https://www.schedulesdirect.org/signup)

Ah, I missed that. If I do an initial setup during the free trial, maybe I can just write down the frequencies & other settings for a few channels to use during testing. I guess I'll try that tonight. Thanks!

> Could you use w_scan to create a channels.conf that you can then use to seed the mythtv tuner/channel scanner?

Nope, w_scan, dvbscan, et al. do not work. I've tried them all in a variety of installations with this card. Nothing picks up any channels.

Thanks everyone! Please keep the suggestions coming.

---

### Post by klc5555 on 2010-08-31
> **MALDATA said:**
> 


After installing the trunk dvb drivers, it still won't unload!

```
root@mythtv:~# rmmod cx18_alsa
root@mythtv:~# rmmod cx18
ERROR: Module cx18 is in use
root@mythtv:~# lsmod | grep cx18
cx18                  109824  1 
dvb_core               85978  1 cx18
cx2341x                12372  1 cx18
v4l2_common            17381  4 cs5345,tuner,cx18,cx2341x
i2c_algo_bit            5028  2 radeon,cx18
videodev               42138  4 cs5345,tuner,cx18,v4l2_common
tveeprom               11038  1 cx18
```



I can't do this until the module unloading problem gets resolved... the script needs to unload and load the module several times.



I did install the drivers successfully, but as you can see above, that didn't change anything.

Please let me know what you think I should do now, and thanks again for all the help!

At this juncture I'd recommend blacklisting the cx18 module so that it doesn't load at all at boot, and then load it by hand from a prompt. You might try also loading it with the radio disabled, i.e.  sudo modprobe cx18 tuner=43 radio=0 (or without the tuner= option, or substituting a different tuner value).If anything odd is going on at this point with the module load, it will turn up at the end of the syslog. Loading the module by hand after the boot may also make it easier to unload it.



I suspect that your tveeprom is not autodetecting the tuner properly, and it is known that the cx18 will cheerfully load to its autodetected defaults no matter what is put in the .conf file in /etc/modprobe.d/  Which is another reason to blacklist the module and try loading it from a prompt instead. In the backend setup, the correctly identified card should appear (at DVB0) as something like "Samsung S5H1409 QAM/8VSB Frontend" or similar.

---

### Post by JMcFly on 2010-08-31
What does the 'tuner=XX' value mean or where does it come from? I'm having some issues with my 1600 (no analog audio, digital doesn't work at all) that I'm trying to solve

---

### Post by MALDATA on 2010-08-31
> **klc5555 said:**
> At this juncture I'd recommend blacklisting the cx18 module so that it doesn't load at all at boot, and then load it by hand from a prompt. You might try also loading it with the radio disabled, i.e.  sudo modprobe cx18 tuner=43 radio=0 (or without the tuner= option, or substituting a different tuner value).If anything odd is going on at this point with the module load, it will turn up at the end of the syslog. Loading the module by hand after the boot may also make it easier to unload it.

That's probably a good idea. How does this work with dependencies? If the cx18 module depends on another module but nothing else does, will the other one still load automatically on boot if cx18 is blacklisted? Just to make sure I understand what's happening.

> **klc5555 said:**
> 
I suspect that your tveeprom is not autodetecting the tuner properly, and it is known that the cx18 will cheerfully load to its autodetected defaults no matter what is put in the .conf file in /etc/modprobe.d/  Which is another reason to blacklist the module and try loading it from a prompt instead. In the backend setup, the correctly identified card should appear (at DVB0) as something like "Samsung S5H1409 QAM/8VSB Frontend" or similar.

In the backend setup, it actually IS identified as "Samsung S5H1409 QAM/8VSB Frontend." Does that really mean it is properly identified, or could something else make that show up also?

Thanks

---

### Post by MALDATA on 2010-08-31
> **JMcFly said:**
> What does the 'tuner=XX' value mean or where does it come from? I'm having some issues with my 1600 (no analog audio, digital doesn't work at all) that I'm trying to solve

From what I've seen, even though they all have the HVR1600 model number, the card may use one of several different tuner chips. That value specifies which chip is on your card. The list is here

[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.tuner]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.tuner")

Of course, as you can see, I'm not necessarily the guy to go to for answers, but that's my impression of the situation.

---

### Post by MALDATA on 2010-08-31
I blacklisted the cx18 driver, so now I can load and unload the cx18 and cx18_alsa modules like you said. However, this doesn't change anything.

Here's the dmesg output when I do that:

```

[  517.216521] cx18-alsa: module unloading...
[  517.225206] cx18-alsa: module unload complete
[  517.244686] cx18-0:  info: Removing Card
[  517.244693] cx18-0:  info: Stopping all streams
[  517.244724] cx18-0:  info: Preparing for firmware halt.
[  517.246020] cx18-0:  info: Deallocating buffers for encoder MPEG stream
[  517.246306] cx18-0: unregister DVB
[  517.246899] cx18-0:  info: Deallocating buffers for TS stream
[  517.246959] cx18-0:  info: Deallocating buffers for encoder YUV stream
[  517.247127] cx18-0:  info: Deallocating buffers for encoder VBI stream
[  517.247283] cx18-0:  info: Deallocating buffers for encoder PCM audio stream
[  517.247693] cx18-0:  info: Deallocating buffers for encoder IDX stream
[  517.247764] cx18-0:  info: Deallocating buffers for encoder radio stream
[  517.248084] tda9887 3-0043: destroying instance
[  517.248166] tuner-simple 3-0061: destroying instance
[  517.248268] cx18-0:  info: releasing enc_mem
[  517.250470] cx18 0000:02:02.0: PCI INT A disabled
[  517.250477] cx18-0: Removed Hauppauge HVR-1600
[  525.849957] cx18:  Start initialization, version 1.4.0
[  525.850035] cx18-0: Initializing card 0
[  525.850042] cx18-0: Autodetected Hauppauge card
[  525.850260] cx18 0000:02:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  525.853337] cx18-0: cx23418 revision 01010000 (B)
[  526.068631] tveeprom 2-0050: Hauppauge model 74551, rev C1A3, serial# 1689302
[  526.068636] tveeprom 2-0050: MAC address is 00:0d:fe:19:c6:d6
[  526.068640] tveeprom 2-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[  526.068644] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[  526.068648] tveeprom 2-0050: audio processor is CX23418 (idx 38)
[  526.068651] tveeprom 2-0050: decoder processor is CX23418 (idx 31)
[  526.068654] tveeprom 2-0050: has radio
[  526.068657] cx18-0: Autodetected Hauppauge HVR-1600
[  526.068661] cx18-0: Simultaneous Digital and Analog TV capture supported
[  526.167631] IRQ 17/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[  526.173920] tuner 3-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[  526.174034] tda9887 3-0043: creating new instance
[  526.174037] tda9887 3-0043: tda988[5/6/7] found
[  526.177295] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[  526.179923] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[  526.183677] tuner-simple 3-0061: creating new instance
[  526.183682] tuner-simple 3-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[  526.183687] tuner-simple 3-0061: tuner 77 atv rf input will be set to input -127373280 (insmod option)
[  526.183690] tuner-simple 3-0061: tuner 77 dtv rf input will be autoselected
[  526.185913] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[  526.185921] DVB: registering new adapter (cx18)
[  526.200673] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-cpu.fw
[  526.324284] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[  526.335854] MXL5005S: Attached at address 0x63
[  526.335865] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[  526.336203] cx18-0: DVB Frontend registered
[  526.336209] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[  526.336315] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[  526.336403] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[  526.336490] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[  526.336495] cx18-0: Initialized card: Hauppauge HVR-1600
[  526.336554] cx18:  End initialization
[  526.366615] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-apu.fw
[  526.379406] cx18-alsa: module loading...
[  526.490900] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[  526.496927] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[  526.708023] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-cpu.fw
[  526.837375] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-apu.fw
[  527.145743] cx18 0000:02:02.0: firmware: requesting v4l-cx23418-dig.fw
[  527.332242] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[  527.351092] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

```

I grepped the dmesg in my first post, but in this full output, you can see that there are a few lines that don't make sense. 

```

[  526.068640] tveeprom 2-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)

[  526.183682] tuner-simple 3-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))

```

According to the list I posted last time, there's no entry for TCL MFNM05-4 as in the tveeprom line.  Tuner-simple seems to set it to Philips NTSC MK3 (FM1236MK3 or FM1236/F). Maybe that's normal and I just don't know what they mean.

Anyway, I tried modprobing all the tuner type values as in this script

```

#!/bin/bash

VIDEO_DEVICE=/dev/video0
CHANNEL=3
FREQUENCY_TABLE=us-bcast

let start=1
let end=84

for ((i=$start; i <= $end; i++))
do
    echo -n "Tuner type $i: "
    modprobe -r cx18_alsa
    modprobe -r cx18
    modprobe cx18 tuner=$i debug=3
    ivtv-tune -t $FREQUENCY_TABLE -c $CHANNEL -d $VIDEO_DEVICE > /dev/null
    v4l2-ctl -T -d $VIDEO_DEVICE | grep 'Signal strength'
    sleep 1
done

```

and the output is basically nothing:

```

Tuner type 1: 	Signal strength/AFC  : 0%/187500
Tuner type 2: 	Signal strength/AFC  : 0%/187500
Tuner type 3: 	Signal strength/AFC  : 0%/187500
Tuner type 4: 	Signal strength/AFC  : 0%/187500
Tuner type 5: 	Signal strength/AFC  : 0%/187500
Tuner type 6: 	Signal strength/AFC  : 0%/187500
Tuner type 7: 	Signal strength/AFC  : 0%/187500
Tuner type 8: 	Signal strength/AFC  : 0%/187500
Tuner type 9: 	Signal strength/AFC  : 0%/187500
Tuner type 10: 	Signal strength/AFC  : 0%/187500
Tuner type 11: 	Signal strength/AFC  : 0%/187500
Tuner type 12: 	Signal strength/AFC  : 0%/187500
Tuner type 13: 	Signal strength/AFC  : 0%/187500
Tuner type 14: 	Signal strength/AFC  : 0%/187500
Tuner type 15: 	Signal strength/AFC  : 0%/187500
Tuner type 16: 	Signal strength/AFC  : 0%/187500
Tuner type 17: 	Signal strength/AFC  : 0%/187500
Tuner type 18: 	Signal strength/AFC  : 0%/187500
Tuner type 19: 	Signal strength/AFC  : 0%/187500
Tuner type 20: 	Signal strength/AFC  : 0%/187500
Tuner type 21: 	Signal strength/AFC  : 0%/187500
Tuner type 22: 	Signal strength/AFC  : 0%/187500
Tuner type 23: 	Signal strength/AFC  : 0%/187500
Tuner type 24: 	Signal strength/AFC  : 0%/187500
Tuner type 25: 	Signal strength/AFC  : 0%/187500
Tuner type 26: 	Signal strength/AFC  : 0%/187500
Tuner type 27: 	Signal strength/AFC  : 0%/187500
Tuner type 28: 	Signal strength/AFC  : 0%/187500
Tuner type 29: 	Signal strength/AFC  : 0%/187500
Tuner type 30: 	Signal strength/AFC  : 0%/187500
Tuner type 31: 	Signal strength/AFC  : 0%/-187500
Tuner type 32: 	Signal strength/AFC  : 0%/187500
Tuner type 33: 	Signal strength/AFC  : 0%/187500
Tuner type 34: 	Signal strength/AFC  : 0%/187500
Tuner type 35: 	Signal strength/AFC  : 0%/187500
Tuner type 36: 	Signal strength/AFC  : 0%/187500
Tuner type 37: 	Signal strength/AFC  : 0%/187500
Tuner type 38: 	Signal strength/AFC  : 0%/187500
Tuner type 39: 	Signal strength/AFC  : 0%/187500
Tuner type 40: 	Signal strength/AFC  : 0%/187500
Tuner type 41: 	Signal strength/AFC  : 0%/187500
Tuner type 42: 	Signal strength/AFC  : 0%/187500
Tuner type 43: 	Signal strength/AFC  : 0%/187500
Tuner type 44: 	Signal strength/AFC  : 0%/187500
Tuner type 45: 	Signal strength/AFC  : 0%/187500
Tuner type 46: 	Signal strength/AFC  : 0%/187500
Tuner type 47: 	Signal strength/AFC  : 0%/187500
Tuner type 48: 	Signal strength/AFC  : 0%/187500
Tuner type 49: 	Signal strength/AFC  : 0%/187500
Tuner type 50: 	Signal strength/AFC  : 0%/187500
Tuner type 51: 	Signal strength/AFC  : 0%/187500
Tuner type 52: 	Signal strength/AFC  : 0%/187500
Tuner type 53: 	Signal strength/AFC  : 0%/187500
Tuner type 54: 	Signal strength/AFC  : 0%/187500
Tuner type 55: 	Signal strength/AFC  : 0%/187500
Tuner type 56: 	Signal strength/AFC  : 0%/187500
Tuner type 57: 	Signal strength/AFC  : 0%/187500
Tuner type 58: 	Signal strength/AFC  : 0%/187500
Tuner type 59: 	Signal strength/AFC  : 0%/187500
Tuner type 60: 	Signal strength/AFC  : 0%/187500
Tuner type 61: 	Signal strength/AFC  : 0%/187500
Tuner type 62: 	Signal strength/AFC  : 0%/187500
Tuner type 63: 	Signal strength/AFC  : 0%/187500
Tuner type 64: 	Signal strength/AFC  : 0%/187500
Tuner type 65: 	Signal strength/AFC  : 0%/187500
Tuner type 66: 	Signal strength/AFC  : 0%/187500
Tuner type 67: 	Signal strength/AFC  : 0%/187500
Tuner type 68: 	Signal strength/AFC  : 0%/187500
Tuner type 69: 	Signal strength/AFC  : 0%/187500
Tuner type 70: 	Signal strength/AFC  : 0%/187500
Tuner type 71: 	Signal strength/AFC  : 0%/-187500
Tuner type 72: 	Signal strength/AFC  : 0%/187500
Tuner type 73: 	Signal strength/AFC  : 0%/187500
Tuner type 74: 	Signal strength/AFC  : 0%/187500
Tuner type 75: 	Signal strength/AFC  : 0%/187500
Tuner type 76: 	Signal strength/AFC  : 0%/187500
Tuner type 77: 	Signal strength/AFC  : 0%/187500
Tuner type 78: 	Signal strength/AFC  : 0%/187500
Tuner type 79: 	Signal strength/AFC  : 0%/187500
Tuner type 80: 	Signal strength/AFC  : 0%/-187500
Tuner type 81: 	Signal strength/AFC  : 0%/187500
Tuner type 82: 	Signal strength/AFC  : 0%/187500
Tuner type 83: 	Signal strength/AFC  : 0%/187500
Tuner type 84: 	Signal strength/AFC  : 0%/187500

```

However, this script uses ivtv-tune to try to connect to "channel 3." Wouldn't I have to change that to some channel that I know is present? And what's the syntax for a digital channel? If my TV has channel 9-1, would I put in 9-1 in ivtv-tune and mythbackend? Or something like 9_1, 9.1, or just plain 9?

Also, I signed up for the free trial of schedulesdirect. The analog input seems to have grabbed a few channels from the lineup, but the digital input (remember, it's just an atsc antenna) doesn't get any channels when I hit the "fetch from source" button in the backend setup (there are several channels listed on the SD website).

I added a few channels manually like JMcFly suggested initially, but I have no way of knowing if it's correct (again, do I set it to channel 9, 9-1, etc.?). If I add channels manually, it accepts them when I click Finish, but if I try to switch to the digital input in the frontend, the screen just goes black and I can't change the channel. I can't tell if the tuner still doesn't work or if I didn't fill in the channel info correctly.

---

### Post by MALDATA on 2010-08-31
Also, I keep forgetting to point out that if I move the antenna over to the analog coax input, I CAN tune to the few analog channels still broadcasting. I get good picture and sound... the weird thing is that the channel number I tune in to is NOT the actual channel number!

For example, one channel still broadcasting in my area is analog channel 26. I can tune into that on my TV. In mythtv, I can tune into that analog channel, but it comes in as channel 23... 26 is just static!

I have no idea what this means.

I have to stop screwing around with this for tonight or I'm gonna lose it.

---

### Post by klc5555 on 2010-09-01
> **MALDATA said:**
> Also, I keep forgetting to point out that if I move the antenna over to the analog coax input, I CAN tune to the few analog channels still broadcasting. I get good picture and sound... the weird thing is that the channel number I tune in to is NOT the actual channel number!

For example, one channel still broadcasting in my area is analog channel 26. I can tune into that on my TV. In mythtv, I can tune into that analog channel, but it comes in as channel 23... 26 is just static!

I have no idea what this means.

I have to stop screwing around with this for tonight or I'm gonna lose it.

Sorry, I'd forgotten that Iglenn's script checks the analog device node /dev/video0 rather than the DVB0 device node.

But, if the card is tuning analog, at least, then my initial suspicion was wrong. The module seems to have satisfactorily  autodetected the tuner type and loaded in usable form. You could test further by changing the script's analog channel to 26 (or 23) and see if any of the other tuner options operate better, but I'm not certain this will make the card work any different on 8-VSB.

I've not used 1600s for digital terrestrial, but have occasionally for clear-QAM on cable. What I had to do to get them to work reasonably on QAM was to hook them up to a good drop-amp, because of their digital signal strength issues relative to other digital cards I use (pchdtv-hd-5500 and the new-style AverMedia 180). I've had to set them up on their own input sources, then, when scanning with the 1600 (still on Mythtv 0.21 --0.22 and 0.23 seem to have broken more than they've fixed) the card would get some channel locks even where signal strength was registering 0%. I'd get more channels (still through a drop-amp) by generating a channels.conf using the dvb scan utility. This would produce a reasonable number of tunable signals for the 1600, but never the full range available to the other digital cards without amplification.

So in summary, the only other idea I have to offer is to see whether a good drop-amp coming off your antenna will clear up some of your digital difficulty. Otherwise, it may be time to think about saving the 1600 for decoding analog input from that eventual cable set-top box, and getting a superior and better linux-supported digital card (like the pchdtv hd-5500, whose digital drivers have worked out-of-the-box since about Ubuntu 7.04) for your digital needs.

Sorry. I know it's incredibly frustrating --maybe someone else will have a better idea.

---

### Post by MALDATA on 2010-09-01
> **klc5555 said:**
> I've had to set them up on their own input sources, then, when scanning with the 1600 (still on Mythtv 0.21 --0.22 and 0.23 seem to have broken more than they've fixed) the card would get some channel locks even where signal strength was registering 0%.

Do you think it's worth downloading an old version, say, mythbuntu 9.04, and giving that a shot? JMcFly seems to recall that scanning worked back then.

I just want to exhaust all possible options before investing in ANOTHER tuner card... and also, should we post some kind of warning on the linuxtv wiki about the 1600 and 1800? The current postings seem a little, shall we say, *optimistic*, and seem to have caused me to make some unwise (and sadly unreturnable) purchases...

---

### Post by JMcFly on 2010-09-01
The 1600 works fine once you get it installed properly (which I will admit is a chore, I remember having lots of problems in 9.04 with it when I built my first backend, the analog side sort of works out of the box in 10.04 but digital is giving me fits), and don't use channel scan as a method of determining card functionality.  Hook it up to basic (analog) cable and an HD antenna, program a few known channel numbers into the backend and see what you get in the front end. 
 
One issue I ran into with 10.04 is the OS boots too quickly, sometimes the 1600's drivers do not load in the proper order so I ended up without analog audio. rmmod/modprobe is one way to fix it, but I haven't figured out how to slow that part of the boot process down so it loads correctly 100% of the time.

---

### Post by MALDATA on 2010-09-01
> **JMcFly said:**
> The 1600 works fine once you get it installed properly (which I will admit is a chore, I remember having lots of problems in 9.04 with it when I built my first backend, the analog side sort of works out of the box in 10.04 but digital is giving me fits), and don't use channel scan as a method of determining card functionality.  Hook it up to basic (analog) cable and an HD antenna, program a few known channel numbers into the backend and see what you get in the front end.

That's one of the problems I'm having. I have no idea how to "program a few known channel numbers into the backend" manually. See a couple posts above. What's the correct syntax for a digital channel? I'm not sure how to verify that I put it in correctly, and it refuses to fetch the listing from SD.

> **JMcFly said:**
> 
One issue I ran into with 10.04 is the OS boots too quickly, sometimes the 1600's drivers do not load in the proper order so I ended up without analog audio. rmmod/modprobe is one way to fix it, but I haven't figured out how to slow that part of the boot process down so it loads correctly 100% of the time.

I tried rmmod/modprobe on the cx18 module (see above), but it didn't help me. There must be something else I'm missing.

Thanks everyone. Please let me know if you have any ideas on what to try next.

---

### Post by JMcFly on 2010-09-01
Again, [[COLOR=#444444]www.antennaweb.org[/COLOR]]("http://www.antennaweb.org/") to find out what digital channels are in your area receivable with your antenna.  In Mythbackend, one of the options (I think its the fifth, going from memory) is channel configuration.  In there you would hit 'add new channel' at the top of the listing and type in a call name (doesn't matter, could be anything), a channel number (important) and channel call sign (doesn't matter).  Add the channels reported by antennaweb closest to you, two or three should suffice.  Digital channels are in the format 'X-Y' so 2-3, 4-10 and 56-9 could be valid channels, but I think antennaweb only reports -1 channels (if you can receive -1 you'll also get -2, -3, etc if broadcast).

---

### Post by MALDATA on 2010-09-01
> **JMcFly said:**
> In there you would hit 'add new channel' at the top of the listing and type in a call name (doesn't matter, could be anything), a channel number (important) and channel call sign (doesn't matter).  Add the channels reported by antennaweb closest to you, two or three should suffice.  Digital channels are in the format 'X-Y' so 2-3, 4-10 and 56-9 could be valid channels, but I think antennaweb only reports -1 channels (if you can receive -1 you'll also get -2, -3, etc if broadcast).

OK, that's what I was looking for. I know I get channel 9-1 with good signal quality on my TV. But I didn't know if I needed to specify the actual frequency or not (If you hit "next" a couple times in the "add new channel" menu, it asks you to put in either the channel or the frequency). Since I still didn't get anything, I couldn't tell if it was because the values I put in weren't in the right format (or if something was missing) or if the tuner still just didn't work.

Thanks for the clarification.

---

### Post by klc5555 on 2010-09-01
> **MALDATA said:**
> Do you think it's worth downloading an old version, say, mythbuntu 9.04, and giving that a shot? JMcFly seems to recall that scanning worked back then.

I just want to exhaust all possible options before investing in ANOTHER tuner card... and also, should we post some kind of warning on the linuxtv wiki about the 1600 and 1800? The current postings seem a little, shall we say, *optimistic*, and seem to have caused me to make some unwise (and sadly unreturnable) purchases...

After all you've already suffered, Mythbuntu 9.04 (the last with 0.21) might be worth a shot. But the cx18 module with the 2.6.28 kernel was seriously broken, both digital and analog, which had a some kind of race condition with playback. So the first thing you'll need to do (after installing headers, kernel source, and gcc) is download/compile the v4l-dvb daily snapshot. With freshly compiled drivers, I've had no particular troubles with the 1600 on Mythbuntu 9.04, other than needing to have the cx18 unload and reload in the /etc/rc.local to guarantee clean analog audio at bootup.

Mythbuntu 9.04 still survives for download directly from the Ubuntu Mothership:  [http://cdimage.ubuntu.com/mythbuntu/releases/9.04/release/](http://cdimage.ubuntu.com/mythbuntu/releases/9.04/release/)

---

### Post by MALDATA on 2010-09-01
> **klc5555 said:**
> With freshly compiled drivers, I've had no particular troubles with the 1600 on Mythbuntu 9.04, other than needing to have the cx18 unload and reload in the /etc/rc.local to guarantee clean analog audio at bootup.

Compared to what I've been working on, that sounds downright delightful. If you claim that this card is working on that setup and we already know that the correct tuner value is being set for my card, then I guess this is the logical next step.

I'll let you know what happens.

Thanks!

---

### Post by JMcFly on 2010-09-02
Two things I found last night:
1. Did you compile any new drivers? The 1600 is natively supported in 10.04 but the wikis have not been updated to state that so when I tried to install my 1600 in my 10.04 system I spent a lot of time trying to compile drivers that already existed.  Basically, start with a fresh 10.04 install, install the firmware and go directly to installing the tuners (if it says to use the 'make' command you're on the wrong path) in the backend.
 
2. Stop the backend via terminal (10.04: "sudo service mythtv-backend stop") and restart it in a terminal window ("mythbackend), look for anything that doesnt look 'right', my system thought the 1600 was a multiplex tuner so the digital was not initializing properly. Do the same for the front end ("mythfrontend") in a second terminal window and you can read all the error codes that may pop up when you hit 'watch live tv' and try to switch between analog and digital tuners.

---

### Post by MALDATA on 2010-09-02
This is a special kind of ridiculous.

I downloaded mythbuntu 9.04 and ran the installer directly (i.e., not by running a live desktop). It looked like it finished ok, then it bounced into the live desktop. I rebooted and grub wasn't installed.

So, I booted into the live cd and installed from the live desktop instead. Again, it seemed to have finished, but grub still wasn't installed when I rebooted.

Then I tried booting into the live desktop again and tried to install grub manually by chrooting into the target install and running grub-install. Still nothing. Can't find the stage1 file.

> Two things I found last night:
1. Did you compile any new drivers? The 1600 is natively supported in 10.04 but the wikis have not been updated to state that so when I tried to install my 1600 in my 10.04 system I spent a lot of time trying to compile drivers that already existed. Basically, start with a fresh 10.04 install, install the firmware and go directly to installing the tuners (if it says to use the 'make' command you're on the wrong path) in the backend.

Honestly, I can't remember. I've tried so many things that I must have tried this initially, but I can't be certain. I think I did. I remember the little pop-up screen that said it needed to install firmware. I think on the first try I just let it do that and hoped for the best.

> 2. Stop the backend via terminal (10.04: "sudo service mythtv-backend stop") and restart it in a terminal window ("mythbackend), look for anything that doesnt look 'right', my system thought the 1600 was a multiplex tuner so the digital was not initializing properly. Do the same for the front end ("mythfrontend") in a second terminal window and you can read all the error codes that may pop up when you hit 'watch live tv' and try to switch between analog and digital tuners.

I *know* I didn't try that. But I guess since I can't even get 9.04 to install properly, maybe I should just fight through it with 10.04.

> my system thought the 1600 was a multiplex tuner so the digital was not initializing properly

Were you able to figure out what was happening and how to fix it? Or is this still an issue?

---

### Post by klc5555 on 2010-09-02
> **JMcFly said:**
> Two things I found last night:
1. Did you compile any new drivers? The 1600 is natively supported in 10.04 but the wikis have not been updated to state that so when I tried to install my 1600 in my 10.04 system I spent a lot of time trying to compile drivers that already existed.  Basically, start with a fresh 10.04 install, install the firmware and go directly to installing the tuners (if it says to use the 'make' command you're on the wrong path) in the backend.
 

The cx18 began to be rolled into the kernel tree with the 2.6.26 and later kernels; i.e. starting with Mythbuntu 8.10. 

The more recent cx18 patches, many dealing with digital signal strength issues, and some dating to as recently as three or four months ago, were intended to be included with the 2.6.33 kernel tree, as I understand it. This is great, save that at the last minute prior to its release, Ubuntu 10.04 got reverted back to kernel 2.6.32. So even in Mythbuntu 10.04 you might want to consider compiling the daily v4l-dvb snapshot from linuxtv.org, unless your particular installation is fortunate enough to have avoided any of the usual problems.

---

### Post by klc5555 on 2010-09-02
> **MALDATA said:**
> 

Then I tried booting into the live desktop again and tried to install grub manually by chrooting into the target install and running grub-install. Still nothing. Can't find the stage1 file.





This is a grub classic: error #15. Grub 0.97's arcane drive nomenclature has failed to properly mesh with the normal drive nomenclature listing the drive/partition that has the kernel image on it. So it's looking for the kernel in the wrong place. Particularly common if the PC has both IDE and SATA drives on it. 

The fix is quite simple and documented lots of places, but very simply in a Ubuntu context in Ralphie's post mid-way through this thread here: [http://webcache.googleusercontent.com/search?q=cache:tZPQKJEeC_MJ:ubuntuforums.org/showthread.php%3Ft%3D297261+grub+error+15+file+not+found&cd=1&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:tZPQKJEeC_MJ:ubuntuforums.org/showthread.php%3Ft%3D297261+grub+error+15+file+not+found&cd=1&hl=en&ct=clnk&gl=us)

---

### Post by MALDATA on 2010-09-02
Unfortunately it's not that simple. The "find" commands in grub didn't find anything, and the /boot directory didn't seem like it had the right contents.

I got frustrated with it and quit after a little while, so maybe I just missed something, but I'll look at it again tonight and see if I can get it going.

---

### Post by JMcFly on 2010-09-02
> **klc5555 said:**
> The cx18 began to be rolled into the kernel tree with the 2.6.26 and later kernels; i.e. starting with Mythbuntu 8.10. 
 
The more recent cx18 patches, many dealing with digital signal strength issues, and some dating to as recently as three or four months ago, were intended to be included with the 2.6.33 kernel tree, as I understand it. This is great, save that at the last minute prior to its release, Ubuntu 10.04 got reverted back to kernel 2.6.32. So even in Mythbuntu 10.04 you might want to consider compiling the daily v4l-dvb snapshot from linuxtv.org, unless your particular installation is fortunate enough to have avoided any of the usual problems.Now that I think about it, I'm running daily builds, not the as-distributed 10.04.
 
 
> **MALDATA said:**
> 
[digital side thought to be multiplex by the backend]
 Were you able to figure out what was happening and how to fix it? Or is this still an issue?I think deleting the card from the backend and re-adding it solved the issue.

---

### Post by MALDATA on 2010-09-02
> **JMcFly said:**
> I think deleting the card from the backend and re-adding it solved the issue.

So, do you have the card completely working in 10.04 then? If so, how?

---

### Post by klc5555 on 2010-09-02
> **MALDATA said:**
> Unfortunately it's not that simple. The "find" commands in grub didn't find anything, and the /boot directory didn't seem like it had the right contents.

I got frustrated with it and quit after a little while, so maybe I just missed something, but I'll look at it again tonight and see if I can get it going.

The right contents? The /boot directory with "grub legacy" 0.97 should include /boot/grub/menu.lst with all the salient information.

I wonder if the 10.04 installed grub2 is still in the mbr. It wouldn't normally occur to anyone to purge grub2 prior to doing the 9.04 install with "grub-legacy". 

If you can boot to the completed 9.04 installation from the mythbuntu CD, maybe the thing to do would be to apt-get and install the package "grub-pc", which will replace the faultily installed package "grub" and update the faulty grub installation from 0.97 to grub2, as detailed in the ubuntu grub2 doc [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 

Otherwise, you may need to bite the bullet and debug the tuner issues in 10.04.

---

### Post by klc5555 on 2010-09-02
> **JMcFly said:**
> Now that I think about it, I'm running daily builds, not the as-distributed 10.04.
 
Well, that's the ticket then! If it works, no matter why, no need to fix it!  :)

---

### Post by MALDATA on 2010-09-02
> **klc5555 said:**
> I wonder if the 10.04 installed grub2 is still in the mbr. It wouldn't normally occur to anyone to purge grub2 prior to doing the 9.04 install with "grub-legacy".

I had problems similar to this a while ago. I installed ubuntu (I don't remember which version) on a PC at work to test some of the hardware. Afterward I had to install Debian on it, but a normal format didn't do the job, I couldn't boot into the new install. In the end I had to do a low-level format before I could get a working install.

That's what I did just before I quit working on it last night, I set it to do a complete one-pass-zeros wipe on the drive, and I'll try installing 9.04 again tonight, possibly.

---

### Post by JMcFly on 2010-09-02
> **MALDATA said:**
> So, do you have the card completely working in 10.04 then? If so, how?
I think this is how I finally got it 100% working:
1. Reinstalled 10.04 (formatted previous system drive as I wasn't sure how much I'd screwed up)
2. Updated to daily builds and restored my 9.10 database
3. Set up 1600 analog in backend, downloaded channel line-up from SD and linked analog tuner to basic cable
4. Ran Mythfill database when I exited the backend
5. Started the frontend and verified the analog tuner worked
6. Set up 1600 digital in backend, couldn't download channel line-up from SD for whatever reason (hit button, no response or indication of attempt from computer), manually entered 54-1 (nearest digital broadcaster to my house) in the channel configuration, went back and set 54-1 as starting channel for the digital tuner
7. Exited, did not run mythfilldatabase
8. Started the frontend, verified I could switch from analog to digital and see channel 54-1.
9. Ran mythfilldatabase, this grabbed all the digital channels and populated the list.
10. Verified digital and analog tuners both were still working, checked recording schedule to make sure digital side was being chosen for appropriate shows.
11. Installed HVR-2250 following instructions from the ~30 page thread on the topic, post 212 I think.
12. Temporarily disabled 1600 digital tuner as I only have one antenna and no splitters, verified upcoming recordings switch to 2250's tuners.
13. Told GF I was done, four days after I'd promised (never tell SWMBO that you'll be done a computer upgrade "in an afternoon")

---

### Post by MALDATA on 2010-09-02
All of that seems like it's completely by-the-book, which is what I was worried about. I'm not sure where in that procedure I could have strayed so far...

If we're both using clean installs of 10.04, HVR1600s, and over-the-air ATSC, I'm not sure where the differences could come in.

OK, so here's what I'm going to do:

1. I'm going to try an older installation of Fedora from around the time the packages would match 9.04, just to try it and also to make sure all the grub problems are truly gone.

2. I'm going to try 9.04 again, if for no other reason than that I refuse to let it win.

3. I'm going to try 10.04 again, following your procedure exactly.

4. Depending on the success or failure of those steps, I'm going to decide if I even want to own a computer anymore.

Thanks

---

### Post by MALDATA on 2010-09-03
> 1. I'm going to try an older installation of Fedora from around the time the packages would match 9.04, just to try it and also to make sure all the grub problems are truly gone.

2. I'm going to try 9.04 again, if for no other reason than that I refuse to let it win.

Didn't help. Got Fedora 10 up and running, ran through the basic myth install, but it had the same problems. Tried going back to 9.04, but it still wouldn't install GRUB correctly.

> 
3. I'm going to try 10.04 again, following your procedure exactly.


> 
1. Reinstalled 10.04 (formatted previous system drive as I wasn't sure how much I'd screwed up)
2. Updated to daily builds and restored my 9.10 database
3. Set up 1600 analog in backend, downloaded channel line-up from SD and linked analog tuner to basic cable
4. Ran Mythfill database when I exited the backend
5. Started the frontend and verified the analog tuner worked


This is **EXACTLY** what I did:
I installed 10.04 from the CD and let it do all of its updates. Then I installed the kernel headers and gcc. I got the latest snapshot of the v4l-dvb drivers and installed them using the default configuration (expect for removing the FireDTV module).

After a reboot, I checked the dmesg log and it looked like cx18 loaded fine. Just to see what happened, I unloaded and reloaded it, but it failed to load properly. For some reason it only loads properly on boot.

After another reboot, I set up the analog tuner in the backend, got the channels from SD, and ran mythfilldatabase. When it was done, I started the frontend, hit Watch TV, and it just sat there saying "Please Wait..." until it eventually went back to the main menu. The terminal output isn't very helpful:

```

mark@mythbox:~/Desktop$ mythfrontend
2010-09-03 13:29:56.457 mythfrontend version:
branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-03 13:29:56.458 Using runtime prefix = /usr
2010-09-03 13:29:56.458 Using configuration directory = /home/mark/.mythtv
2010-09-03 13:29:57.149 Empty LocalHostName.
2010-09-03 13:29:57.150 Using localhost value of mythbox
2010-09-03 13:29:57.158 New DB connection, total: 1
2010-09-03 13:29:57.162 Connected to database 'mythconverg' at host: localhost
2010-09-03 13:29:57.163 Closing DB connection named 'DBManager0'
2010-09-03 13:29:57.179 ScreenSaverX11Private: XScreenSaver support enabled
2010-09-03 13:29:57.182 DPMS is disabled.
2010-09-03 13:29:57.184 Primary screen: 0.
2010-09-03 13:29:57.185 Connected to database 'mythconverg' at host: localhost
2010-09-03 13:29:57.186 Using screen 0, 1360x768 at 0,0
2010-09-03 13:29:57.200 Desktop video mode: 1360x768 60.0168 Hz
2010-09-03 13:29:57.417 MythUI Image Cache size set to 20971520 bytes
2010-09-03 13:29:57.440 Enabled verbose msgs:  important general
2010-09-03 13:29:57.449 Primary screen: 0.
2010-09-03 13:29:57.449 Using screen 0, 1360x768 at 0,0
2010-09-03 13:29:57.450 Using theme base resolution of 1280x720
2010-09-03 13:29:57.459 LIRC, Error: Failed to connect to Unix socket
'/dev/lircd'
                       eno: No such file or directory (2)
2010-09-03 13:29:57.460 JoystickMenuThread Error: Joystick disabled -
Failed to read /home/mark/.mythtv/joystickmenurc
2010-09-03 13:29:57.517 Using Frameless Window
2010-09-03 13:29:57.517 Using Full Screen Window
2010-09-03 13:29:57.744 Using the Qt painter
2010-09-03 13:29:57.923 XMLParseBase: Loaded base theme from
'/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-03 13:29:57.943 XMLParseBase: Loaded base theme from
'/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-03 13:29:57.963 XMLParseBase: Loaded base theme from
'/usr/share/mythtv/themes/default/base.xml'
2010-09-03 13:29:57.964 XMLParseBase, Error: Unable to load window
'backgroundwindow' from base
2010-09-03 13:29:57.989 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-03 13:29:58.549 Registering Internal as a media playback plugin.
2010-09-03 13:29:58.591 Cannot load language en_us for module mytharchive
2010-09-03 13:29:58.635 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-03 13:29:58.636 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-03 13:29:58.636 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-03 13:29:58.637 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-03 13:29:58.638 Cannot load language en_us for module mythgallery
2010-09-03 13:29:58.641 Cannot load language en_us for module mythmovies
2010-09-03 13:29:58.668 Current MythMusic Schema Version
(MusicDBSchemaVer): 1017
2010-09-03 13:29:58.734 MonitorRegisterExtensions(0x40,
mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-03 13:29:58.744 Cannot load language en_us for module mythmusic
2010-09-03 13:29:58.759 Current MythVideo Schema Version
(mythvideo.DBSchemaVer): 1032
2010-09-03 13:29:58.805 Cannot load language en_us for module mythvideo
2010-09-03 13:29:58.814 Cannot load language en_us for module mythweather
2010-09-03 13:29:58.821 XMLParseBase: Loading window theme from
/usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-03 13:29:58.930 Loading menu theme from
/usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-09-03 13:29:58.934 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-03 13:29:59.579 MythContext: Connecting to backend server:
127.0.0.1:6543 (try 1 of 1)
2010-09-03 13:29:59.581 Using protocol version 56
2010-09-03 13:30:01.201 TV: Attempting to change from None to WatchingLiveTV
2010-09-03 13:30:01.201 MythContext: Connecting to backend server:
127.0.0.1:6543 (try 1 of 1)
2010-09-03 13:30:01.202 Using protocol version 56
2010-09-03 13:30:01.219 Spawning LiveTV Recorder -- begin
2010-09-03 13:30:01.345 Spawning LiveTV Recorder -- end
2010-09-03 13:30:01.349 ProgramInfo(): Updated pathname '':'' ->
'1023_20100903133001.nuv'
2010-09-03 13:30:01.356 We have a
playbackURL(/var/lib/mythtv/livetv/1023_20100903133001.nuv) &
cardtype(V4L)
2010-09-03 13:30:01.359 We have a RingBuffer
2010-09-03 13:30:41.420 TV Error: StartRecorder() -- timed out waiting
for recorder to start
2010-09-03 13:30:41.420 TV Error: LiveTV not successfully started
2010-09-03 13:30:44.179 Deleting UPnP client...
mark@mythbox:~/Desktop$

```

Unreal.

---

### Post by klc5555 on 2010-09-03
The 6th line from the bottom of the terminal output suggests that the analog half of the card was set up as v4l analog in the backend. If so, it needs to be changed to MPEG2 type. v4l won't run.

---

### Post by MALDATA on 2010-09-03
> **klc5555 said:**
> The 6th line from the bottom of the terminal output suggests that the analog half of the card was set up as v4l analog in the backend. If so, it needs to be changed to MPEG2 type. v4l won't run.

Sorry, fixed that. Now I'm back to the same problem, analog, but no digital. 

> 5. Started the frontend and verified the analog tuner worked
6. Set up 1600 digital in backend, couldn't download channel line-up from SD for whatever reason (hit button, no response or indication of attempt from computer), manually entered 54-1 (nearest digital broadcaster to my house) in the channel configuration, went back and set 54-1 as starting channel for the digital tuner
7. Exited, did not run mythfilldatabase
8. Started the frontend, verified I could switch from analog to digital and see channel 54-1.

I did this and set up a digital channel that I know is there... 9-1. Still no luck. Just to be sure: It asks for the channel number twice in the channel editor, once on the first page and again on the third. In BOTH cases I put 9-1.

I can tune in analog, but if I try to switch to the digital input, it just hangs until I kill it.

The myth output now looks like this. 

```
mark@mythbox:~/Desktop$ mythfrontend
2010-09-03 17:24:25.403 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-03 17:24:25.404 Using runtime prefix = /usr
2010-09-03 17:24:25.404 Using configuration directory = /home/mark/.mythtv
2010-09-03 17:24:26.095 Empty LocalHostName.
2010-09-03 17:24:26.095 Using localhost value of mythbox
2010-09-03 17:24:26.103 New DB connection, total: 1
2010-09-03 17:24:26.108 Connected to database 'mythconverg' at host: localhost
2010-09-03 17:24:26.110 Closing DB connection named 'DBManager0'
2010-09-03 17:24:26.130 ScreenSaverX11Private: XScreenSaver support enabled
2010-09-03 17:24:26.137 DPMS is disabled.
2010-09-03 17:24:26.140 Primary screen: 0.
2010-09-03 17:24:26.140 Connected to database 'mythconverg' at host: localhost
2010-09-03 17:24:26.142 Using screen 0, 1440x900 at 0,0
2010-09-03 17:24:26.157 Desktop video mode: 1440x900 59.891 Hz
2010-09-03 17:24:26.382 MythUI Image Cache size set to 20971520 bytes
2010-09-03 17:24:26.411 Enabled verbose msgs:  important general
2010-09-03 17:24:26.423 Primary screen: 0.
2010-09-03 17:24:26.423 Using screen 0, 1440x900 at 0,0
2010-09-03 17:24:26.424 Using theme base resolution of 1280x720
2010-09-03 17:24:26.433 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-09-03 17:24:26.434 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2010-09-03 17:24:26.492 Using Frameless Window
2010-09-03 17:24:26.492 Using Full Screen Window
2010-09-03 17:24:26.755 Using the Qt painter
2010-09-03 17:24:26.963 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-03 17:24:26.981 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-03 17:24:27.005 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-03 17:24:27.005 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-03 17:24:27.017 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-03 17:24:27.581 Registering Internal as a media playback plugin.
2010-09-03 17:24:27.623 Cannot load language en_us for module mytharchive
2010-09-03 17:24:27.667 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-03 17:24:27.667 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-03 17:24:27.668 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-03 17:24:27.669 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-03 17:24:27.669 Cannot load language en_us for module mythgallery
2010-09-03 17:24:27.673 Cannot load language en_us for module mythmovies
2010-09-03 17:24:27.699 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-03 17:24:27.765 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-03 17:24:27.778 Cannot load language en_us for module mythmusic
2010-09-03 17:24:27.791 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-03 17:24:27.839 Cannot load language en_us for module mythvideo
2010-09-03 17:24:27.849 Cannot load language en_us for module mythweather
2010-09-03 17:24:27.852 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-03 17:24:27.958 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-09-03 17:24:27.961 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-03 17:24:28.767 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-09-03 17:24:28.769 Using protocol version 56
2010-09-03 17:24:30.484 TV: Attempting to change from None to WatchingLiveTV
2010-09-03 17:24:30.484 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-09-03 17:24:30.485 Using protocol version 56
2010-09-03 17:24:30.597 Spawning LiveTV Recorder -- begin
2010-09-03 17:24:30.686 Spawning LiveTV Recorder -- end
2010-09-03 17:24:30.690 ProgramInfo(): Updated pathname '':'' -> '1023_20100903172430.mpg'
2010-09-03 17:24:30.695 We have a playbackURL(/var/lib/mythtv/livetv/1023_20100903172430.mpg) & cardtype(MPEG)
2010-09-03 17:24:31.942 We have a RingBuffer
2010-09-03 17:24:32.761 AFD: Opened codec 0xb398acd0, id(MPEG2VIDEO) type(Video)
2010-09-03 17:24:32.761 AFD: codec MP2 has 2 channels
2010-09-03 17:24:32.761 AFD: Opened codec 0xb398b970, id(MP2) type(Audio)
2010-09-03 17:24:32.951 AO: Using resampler. From: 32000 to 48000
2010-09-03 17:24:32.951 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-03 17:24:32.952 Opening ALSA audio device 'default'.
2010-09-03 17:24:32.961 AO: Using resampler. From: 32000 to 48000
2010-09-03 17:24:32.961 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-03 17:24:32.962 Opening ALSA audio device 'default'.
2010-09-03 17:24:33.002 AO: Using resampler. From: 32000 to 48000
2010-09-03 17:24:33.002 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-03 17:24:33.003 Opening ALSA audio device 'default'.
2010-09-03 17:24:33.048 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2010-09-03 17:24:33.061 ProgramInfo(): Updated pathname '':'' -> '1023_20100903172430.mpg'
2010-09-03 17:24:33.097 OSD Theme Dimensions W: 1280 H: 720
2010-09-03 17:24:33.115 New DB connection, total: 2
2010-09-03 17:24:33.116 Connected to database 'mythconverg' at host: localhost
2010-09-03 17:24:33.120 ProgramInfo(): Updated pathname '':'' -> '1023_20100903172430.mpg'
2010-09-03 17:24:33.177 ProgramInfo(): Updated pathname '':'' -> '1023_20100903172430.mpg'
2010-09-03 17:24:33.234 ProgramInfo(): Updated pathname '':'' -> '1023_20100903172430.mpg'
2010-09-03 17:24:33.291 ProgramInfo(): Updated pathname '':'' -> '1023_20100903172430.mpg'
2010-09-03 17:24:33.309 TV: Changing from None to WatchingLiveTV
2010-09-03 17:24:33.309 TV: State is LiveTV & mctx == ctx
2010-09-03 17:24:33.309 New DB connection, total: 3
2010-09-03 17:24:33.310 Connected to database 'mythconverg' at host: localhost
2010-09-03 17:24:33.313 Realtime priority would require SUID as root.
2010-09-03 17:24:33.314 TV: UpdateOSDInput done
2010-09-03 17:24:33.315 TV: UpdateLCD done
2010-09-03 17:24:33.315 TV: ITVRestart done
2010-09-03 17:24:33.323 [mpeg2video @ 0x46c6960]warning: first frame is no keyframe
2010-09-03 17:24:33.335 [mpeg2video @ 0x46c6960]warning: first frame is no keyframe
2010-09-03 17:24:33.346 Video timing method: DRM
2010-09-03 17:24:40.208 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/schedule-ui.xml
2010-09-03 17:24:46.221 TV Error: Unknown menu action selected: 
2010-09-03 17:24:48.827 [mp2 @ 0x46c6960]incomplete frame
2010-09-03 17:24:48.827 AFD Error: Unknown audio decoding error
2010-09-03 17:24:50.299 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-09-03 17:24:50.300 Using protocol version 56
2010-09-03 17:24:50.423 ProgramInfo(): Updated pathname '':'' -> '1023_20100903172430.mpg'
Killed

```

---

### Post by klc5555 on 2010-09-03
I'm not sure I can help you here. My experience has been that the digital half of the 1600 works only to the extent that it can tune to the correct frequencies. These have to be supplied either by mythtv's own scan, or from a channels.conf file built with non-mythtv tools like dvbscan or w_scan. If none of these methods work, then the 1600 is just not receiving usably strong signals.

---

### Post by NeddyDownUnder on 2010-09-03
Ignore this post if you already know this, or it does not apply to this situation. I didn't read the whole thread as it's pretty long...

 I had quite a bit of trouble getting my TV tuner to work, in the end all I had to do was install the non-free firmware.

```
sudo apt-get install linux-firmware-nonfree
```

Then reboot, pretty simple, but took me a while to find this out.

---

### Post by MALDATA on 2010-09-04
> **NeddyDownUnder said:**
> Ignore this post if you already know this, or it does not apply to this situation. I didn't read the whole thread as it's pretty long...

 I had quite a bit of trouble getting my TV tuner to work, in the end all I had to do was install the non-free firmware.

```
sudo apt-get install linux-firmware-nonfree
```

Then reboot, pretty simple, but took me a while to find this out.

I gave it a shot, but sadly that didn't change anything. Thanks for the suggestion, though!

[QUOTE=kcl5555]I'm not sure I can help you here. My experience has been that the digital half of the 1600 works only to the extent that it can tune to the correct frequencies. These have to be supplied either by mythtv's own scan, or from a channels.conf file built with non-mythtv tools like dvbscan or w_scan. If none of these methods work, then the 1600 is just not receiving usably strong signals.[/QUOTE]

Well, I know those channels are there and the signal is strong enough that it comes through artifact-free on my TV. I played with it for a while tonight and tried various things, but no luck. The analog half of the card works fine, and the digital half SEEMS fine, but I just can't get anything.

Sounds like you're out of ideas. Thanks for all the help!

---

### Post by klc5555 on 2010-09-04
Well, at the current state of the cx18 driver, the card over the near term simply isn't going to be anywhere near as sensitive (on Linux) as your digital TV. For that reason, the one last suggestion I have is to get a good little drop amp, Motorola or PCT, and then use dvbscan or w_scan (both of which are more sensitive than the Mythtv scan, even when the latter is working correctly) to try to generate a channels.conf. Many (though admittedly not all) users who have success with this card rely on a drop amp for digital.

Otherwise, you're right. I'm fresh out of ideas. :sad:

---

### Post by MALDATA on 2010-09-05
> Well, at the current state of the cx18 driver, the card over the near term simply isn't going to be anywhere near as sensitive (on Linux) as your digital TV. For that reason, the one last suggestion I have is to get a good little drop amp, Motorola or PCT, and then use dvbscan or w_scan (both of which are more sensitive than the Mythtv scan, even when the latter is working correctly) to try to generate a channels.conf. Many (though admittedly not all) users who have success with this card rely on a drop amp for digital.

Well, I really didn't want to spend any more money on this project, but this is apparently the last resort. I picked up this amp:

[http://www.amazon.com/Motorola-Booster-484095-001-00-Bi-Directional-Amplifier/dp/B000066E6Y/ref=pd_cp_e_1]("http://www.amazon.com/Motorola-Booster-484095-001-00-Bi-Directional-Amplifier/dp/B000066E6Y/ref=pd_cp_e_1")

I'll give it a try when it gets here in a couple days and I'll let you know. I guess it never really occurred to me that the card's ability to find a signal would be a property of the driver... I figured if the signal is strong enough for one receiver it should be strong enough for another.

One thing I'm concerned about though... from way back in post #2,

> Scan function hasn't worked since at least 9.04 IIRC

I assume this means that the scan function of MythTV hasn't worked... not that the card can't scan at all, right? In other words, if the drop amp helps, I can expect dvbscan to actually work in 10.04?

---

### Post by klc5555 on 2010-09-06
Mythtv scan was what was reputed to be broken. Either dvbscan or w_scan should work fine, and are more sensitive than mythtv scan, even when the latter is working correctly. And (if it could get any more annoying) the 1600 card may actually be getting usable signal locks even when the signal strength is being reported as zero or almost zero.

The cx18 driver controlling the level of amplification the digital tuner is set to provide has always been one of the main problems. Since Hauppauge themselves actually bother to code their own Windows drivers for their products, the Windows installations of this card (with Sage tv or what have you) seem to be free from nearly all of the problems that bedevil the 1600 under Linux. Trouble is, most Linux users don't realize what they may be getting themselves into until they already own the card.

---

### Post by MALDATA on 2010-09-11
I can't explain it, but the amplifier actually makes it worse. I get fewer channels on the TV with it than I do without it. No change to the situation on the computer.

I'm pretty much done fighting with these things. Thanks for the help, though!

---

### Post by Quadari on 2010-09-22
Hi All,

I'm hoping to pseudo re-open this thread, since I'm having somewhat similar problems.  Let me give you the setup:

I have an HVR-1600 card, and it's the one with the three inputs, FM, "TV In", and "ANT In".  From what I've read everywhere the "TV in" is the analog signal, and the "ANT In" is the digital signal.

Now, since analog signals don't really exist anymore (given the switch to digital TV and Comcast's recent switch to (I think) all digital cable, at least in the Chicago area, where I'm at) I'm not concerned about getting the analog part to work.

As far as getting the digital signal to work, here's the situation.  I don't have an HDTV antenna, but I don't pay for cable TV either.  There's a cable coming into my apartment from the outside world, and when I plug that cable into the back of my LG LCTV I get (what I think is) HD clear QAM broadcasts of all of the local channels.  I used to pick up some random non-HD cable channels also, but that stopped recently.  When I plug the cable into the back of the TV channels appear without any hassle.  I've plugged that same cable into the "ANT In" port on the hvr-1600.

I finally got all my hardware yesterday, so have been trying to set it up without success.  I started with a blank hard drive, and did a clean install of mythbuntu 10.04.  The backend successfully probed the hauppauge hvr-1600 card, and I set it up as a DVB DTV capture card (v3.x), which it recognized as the "Samsung SSH1409" as it is supposed to according to other posts.

I signed up for trial of schedulesdirect, but I can't quite figure out which lineup to use because while I only get the broadcast channels, I'm not getting them over-the-air.  I think I had some success finding channels when I set my lineup as Comcast Digital Cable.  

However, when I run the mythtv frontend and click "watch tv" it either says "Wait..." and then goes back to the frontend main screen with no error.  Or sometimes it has an error which says "MythTV is currently using all inputs, but there are no active recordings."

I've been fiddling around with things almost endlessly with no success in actually watching tv, so any and all help is appreciated.

Thanks,
Q

---

### Post by MALDATA on 2010-09-22
Hey Quadari,

You are in fact having the exact same problem I was, with the same hardware (and in Chicago, as well). I have had no luck at all with it.

I bought a pcHDTV card, and the thing has worked flawlessly, although I abandoned MythTV because I don't want a standalone box... I was just trying to use it under the assumption that it would be easier to set up. I still have the 1600, though, so if you can get it to work and let me know how, then at least I can make some use of it.

I can give you my channels.conf file for the over-the-air channels in Chicago, but if you're not using an antenna then I don't know if it'll work. Are you sure it's clearQAM and not ATSC?

---

### Post by Quadari on 2010-09-22
> **MALDATA said:**
> 
I can give you my channels.conf file for the over-the-air channels in Chicago, but if you're not using an antenna then I don't know if it'll work. Are you sure it's clearQAM and not ATSC?

Hello, hello.

I'm definitely note sure that it's clearQAM and not ATSC, that was just (for some reason) my impression.  But I could certainly be wrong about that, so I defer to anyone who is more knowledgeable about this series-of-tubes through which television passes.

I certainly would take the channels.conf file.  Can't hurt to play with it.  I'll PM you my email address.

---

### Post by MALDATA on 2010-09-22
> **Quadari said:**
> 
I'm definitely note sure that it's clearQAM and not ATSC, that was just (for some reason) my impression.  But I could certainly be wrong about that, so I defer to anyone who is more knowledgeable about this series-of-tubes through which television passes.


I think I remember hearing someone say that a building's wiring can act as a (crappy) antenna. Depending on whether or not that's true, those could be ATSC signals. It might not be, in which case you're just getting clearQAM. If you're getting ALL of the broadcast stations with strong signals, then it's probably clearQAM.

---

### Post by Quadari on 2010-09-23
So I got my HVR-1600 (sort of) working last night.  Here's what I did:

I first basically followed the directions for "Testing Your DVB Card" on this page:
[http://parker1.co.uk/mythtv_dvb.php]("http://parker1.co.uk/mythtv_dvb.php")
In combination with some of the help on this page
[http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards]("http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards")
Note that the creator of the first link above is in the UK, so I had to modify things slightly since I'm in the US.


The scan returned a whole ton of channels being found, so I knew that the card was working.  :)
I then had to follow the instructions here:
[http://www.mythtv.org/wiki/DVB_search]("http://www.mythtv.org/wiki/DVB_search")
In order to get my channels.conf in a workable format.

After that, I could use mplayer to watch channels (at least the unencrypted ones.  I had to try a bunch of channels totally randomly until I found an unencrypted one, so don't despair if the first channel you try with mplayer doesn't work).  Upon knowing that this all worked, I opened up the mythtv backend setup and set it up to not download any program guide info from schedules direct (since I figured that would just confuse things), and I imported my channels.conf file.  (This took a bit of time.)

Then I closed the backend setup and opened up the mythtv frontend.  Now when I watch live tv it (sort of) works.

Here are my "sort of" qualifications:
[LIST=1]
[*]  Not all of the channels I imported from my channels.conf are real channels.  Most of them are encrypted.  Tonight I'm going to run the scan.sh script from here:
[http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards#Verifying_channel_tuning]("http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards#Verifying_channel_tuning")
in order to get rid of all the encrypted channels.
[*]  HD channels don't really work.  I can sometimes get them to work using mplayer from the command line, if I tell mplayer all sorts of special instructions (like -nocache and -ni, etc.)  But they don't work in the mythtv frontend.  I think this is just because the horsepower of my machine isn't big enough to actually handle HD channels.  Watching standard definition channels seems to work; I can watch, pause, fast forward, etc.  But I get all sorts of weird errors both from Myth and crashes from my GPU when I try to watch HD channels.  That seems to be a separate topic, so I'm going to write a different post about that issue.
[*] I don't yet have any channel names or any program guide info, so in order to find channels that work I just have to blindly surf around.  After I get everything else working I have to figure out how to get the schedules direct data to sync up to my channels that I actually get.
[/LIST]

So that's the news for now.

---

### Post by MALDATA on 2010-09-23
Wow... that was fast. I feel dumb that I can't get mine working.

Can you explain a little more in-depth what you did differently this time compared to your previous attempts? Nothing on those links jumps out at me as being particularly different from what I had already tried.

---

### Post by Quadari on 2010-09-23
> **MALDATA said:**
> Wow... that was fast. I feel dumb that I can't get mine working.

Can you explain a little more in-depth what you did differently this time compared to your previous attempts? Nothing on those links jumps out at me as being particularly different from what I had already tried.


Haha, man, don't feel dumb.  You sometime just have to hold your breath in the right way to get these things to work.  :wink:


In previous attempts I had never tried running the "scan" function, as described on that "Testing your DVB Card" page. I had only tried setting and scanning the channel lineup from within the mythtv backend, and that wasn't going anywhere. So I opened up a terminal, stopped the myth backend, and I ran:

```

scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 | tee channels.conf
```

Then I started actually getting things spat out into a channels.conf file.  I also ran

```

scan /usr/share/dvb/atsc/us-Cable-HRC-center-frequencies-QAM256 | tee channels.conf
```

I can't remember which one ended up working for me.  It depends on the cable carrier.

I then looked at the channels.conf file that was created and noticed that the names of the channels (which is the first column before the ":" in the file) were wrapped in square brackets, like this:
```
[0006]:657000000:QAM_256:74:75:6
[000c]:657000000:QAM_256:0:80:12
```
So that wasn't going to work, based on the information from here:
[http://www.mythtv.org/wiki/DVB_search](http://www.mythtv.org/wiki/DVB_search)

So I ran the suggested command on that page, to change all those bracketed names to just numbers:
```
perl -pe 's/^.{6}/++$i/e;' channels.conf > channels.conf.new
```

Then when I ran:
```
mplayer dvb://1
```
A magical window popped onto the screen and started playing the tv channel.  (To be exact, there were some other flags I had to pass to mplayer, but I can't remember them right now, and don't have access to my terminal shell history, so when I get home later I can edit this.)

After this happened, I was happy because I knew that the card was actually working, so I went and ate dinner.  :)

The next step was just a matter of importing the corrected channels.conf file into mythtv.

Hopefully that should help you some, but I'm happy to try and provide more clarification if I can.

---

### Post by MALDATA on 2010-09-23
I noticed that on that one page you linked to, it says you need to stop the backend before scanning. I wonder if that's why my scans using dvbscan and w_scan never worked... I can't remember whether or not I stopped the backend before trying.

> However, when I run the mythtv frontend and click "watch tv" it either says "Wait..." and then goes back to the frontend main screen with no error. Or sometimes it has an error which says "MythTV is currently using all inputs, but there are no active recordings."

This happened to me as well when I put in channels manually (hangs on the wait screen when you try to watch live tv). Does this still happen to you, or have you only tried to get it to work through mplayer?

---

### Post by Quadari on 2010-09-23
> **MALDATA said:**
> 
This happened to me as well when I put in channels manually (hangs on the wait screen when you try to watch live tv). Does this still happen to you, or have you only tried to get it to work through mplayer?

No - it doesn't happen anymore.  I cleared out all the old channel inputs I had put into the mythtv backend and just imported the channels.conf.  Now when I try to watch live tv it works, subject to the oddities I mentioned above.  It still says "Please wait..." for a few seconds and then a picture pops up (assuming I'm tuned to a real channel.)

---

### Post by MALDATA on 2010-09-24
I tried again last night, but still had no luck.

Using the channels.conf I generated using the working pcHDTV card, I tried to import the channels, but it still tries to scan for them when you hit "Next" and of course it fails to find anything.

When I try to just watch from mplayer (mplayer dvb://WGN-DT), nothing happens. It just sits there until I hit Ctrl-C.

dvbscan /usr/share/dvb/atsc/us-ATSC-whatever just responds with an error that says something about not being able to contact the frontend or something. I had stopped the mythbackend service, and the device nodes for adapter0 were properly created in /dev/dvb, but still nothing.

---

### Post by doogiekd on 2012-01-03
friends, 

i got my hvr-1600 to work by doing the following:

1. download the driver & firmware from: [http://ivtvdriver.org/index.php/Download](http://ivtvdriver.org/index.php/Download)

direct download address of driver: [http://dl.ivtvdriver.org/ivtv/archiv...-0.10.6.tar.gz](http://dl.ivtvdriver.org/ivtv/archiv...-0.10.6.tar.gz)

direct download of firmware: [http://dl.ivtvdriver.org/ivtv/firmwa...irmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmwa...irmware.tar.gz)

2. extract both files by right clicking and selecting "extract" 
an error may appear indicating: 
"this does not look like a .tar archive."

the workaround to extract both the firmware and driver files is:
a. install gunzip. from terminal enter: sudo apt-get install gunzip

b. after gunzip is installed, open terminal and change directory to where both files are - usually desktop. ex: cd \Desktop. 

c. enter in terminal: gunzip filename.tar.gz (replacing file name with the name of driver. enter this command again to do the same for the firmware. ex. sudo gunzip ivtv-firmware.tar.gz & sudo gunzip ivtv-0.10.6.tar.gz

d. change permissions of both files by entering in terminal:
sudo tar xvzf filename.tar - replacing filname with both the driver file and firmware file as described above.

e. once extracted, in terminal change to the directory of the driver file (usually cd \Desktop\ivtv-0.10.6.tar.gz

f. enter sudo build. program will install. let finish and do not interrupt the process.

g. install the firmware. in terminal enter sudo nautilus. be careful, errors doing sudo nautilus can be deadly to your system. (gksu did not work for me here).

h. the root file manager will open. move all files AS INDIVIDUAL FILES (not the folder) from the FIRMWARE directory to \lib\firmware. some firmware files are the same in both the ivtv driver and ivtv firmware folders. just copy all of them as individual files and choose replace when prompted. yes, the ivtv driver will contain some firmware files.

i. close the terminal and nautilus.

j. open the app: STARTUP APPLICATIONS.

K. in startup applications, click ADD. 

l. enter "tv tuner card detect" in the DESCRIPTION field.

m. enter the following in the command field:
ivtv-tune -t us-bcast -c 3 -d /dev/video0

you may have another location for your tv tuner card - video1, ect...

n. shut down your computer.

o. add a coaxial splitter from the output of your cable box. one end will connect to your tv, the other end will connect to the ANALOG input of your tv tuner card.

p. turn on the computer. your tv tuner card should now work. try first in movie player and vlc.

q. go to /dev/video0 (or video1, ect), right click on the tv tuner card and select open with movie player.

r. yes, you will only receive the channel that the cable box is currently set to only.

s. tv-viewer in my opinion is the best app for single recording. add the tv-viewer ppa to your software sources. in terminal type:
sudo deb [http://ppa.launchpad.net/blueyed/ppa/ubuntu](http://ppa.launchpad.net/blueyed/ppa/ubuntu) oneiric main

t. update software sources by entering in terminal: 
sudo apt-get update

u. install tv-viewer from synaptic.

v. IMPORTANT: you will probably have to repeat most of these steps after EVERY kernel update.

enjoy, doogiekd.

---

### Post by thatguruguy on 2012-01-03
a. It's not necessary to post the same thing in several different threads, many of which have been dead over a year, and one of which has been marked "solved."

b. If people wanted tv-viewer to record shows, they'd be using it. This forum is meant to support mythbuntu.

---

