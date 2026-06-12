---
title: "Need help with Hauppauge HVR 4000 and Ubuntu 9.4"
date: 2009-05-19
forum: Multimedia Software
---

### Post by neon-knight on 2009-05-19
Hi,
I'm kind a desperate now, after having no success trying to install HVR 4000. All I found searching internet is old or didn't work for me. I'm running Ubuntu 9.04 with kernel 2.6.28-11-generic which should have support for HVR 4000. I tried to install v4l driver and firmware, without success. Basically I need just analog TV for now, but when I thought everything is OK, I steel had problems trying to scan for channels.
If someone has more experience and know the way to help me (working driver and firmware) please help.

Please see dmesg output, it shows some problems, but I don't know how to solve it.

lspci
```

0a:0a.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0a:0a.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
0a:0a.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
0a:0a.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)

```dmesg
```

[   10.070462] Linux video capture interface: v2.00
[   10.131999] iTCO_vendor_support: vendor-support=0
[   10.142341] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.142541] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x1060)
[   10.142635] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.233001] cx2388x alsa driver version 0.0.7 loaded
[   10.233055] cx88_audio 0000:0a:0a.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.233734] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,autodetected], frontend(s): 2
[   10.233738] cx88[0]: TV tuner type 63, Radio tuner type -1
[   10.237284] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   10.244414] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   10.251276] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.354122] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[   10.405064] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   10.412426] tda9887 0-0043: creating new instance
[   10.412430] tda9887 0-0043: tda988[5/6/7] found
[   10.415853] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   10.443424] tveeprom 0-0050: Hauppauge model 69009, rev B2D3, serial# 5243951
[   10.443428] tveeprom 0-0050: MAC address is 00-0D-FE-50-04-2F
[   10.443431] tveeprom 0-0050: tuner model is Philips FMD1216MEX (idx 133, type 78)
[   10.443434] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   10.443437] tveeprom 0-0050: audio processor is CX882 (idx 33)
[   10.443440] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[   10.443442] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   10.443445] cx88[0]: hauppauge eeprom: model=69009
[   10.453550] tuner-simple 0-0061: creating new instance
[   10.453555] tuner-simple 0-0061: type set to 78 (Philips FMD1216MEX MK3 Hybrid Tuner)
[   10.456214] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:0a:0a.1/input/input5
[   10.457218] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   10.458180] cx88[0]/2: cx2388x 8802 Driver Manager
[   10.458194] cx88-mpeg driver manager 0000:0a:0a.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.458204] cx88[0]/2: found at 0000:0a:0a.2, rev: 5, irq: 21, latency: 49, mmio: 0xd2000000
[   10.458621] cx8800 0000:0a:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.458628] cx88[0]/0: found at 0000:0a:0a.0, rev: 5, irq: 21, latency: 165, mmio: 0xd0000000
[   10.469972] wm8775 0-001b: chip found @ 0x36 (cx88[0])
[   10.474384] cx88[0]/0: registered device video0 [v4l2]
[   10.474465] cx88[0]/0: registered device vbi0
[   10.474528] cx88[0]/0: registered device radio0
[   10.509730] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   10.509735] cx88/2: registering cx8802 driver, type: dvb access: shared
[   10.509739] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[   10.509742] cx88[0]/2: cx2388x based DVB/ATSC card
[   10.509744] cx8802_alloc_frontends() allocating 2 frontend(s)
[   10.532846] cx24116_readreg: reg=0xff (error=-6)
[   10.533343] cx24116_readreg: reg=0xfe (error=-6)
[   10.533345] Invalid probe, probably not a CX24116 device
[   10.546049] tuner-simple 0-0061: attaching existing instance
[   10.546054] tuner-simple 0-0061: couldn't set type to 63. Using 78 (Philips FMD1216MEX MK3 Hybrid Tuner) instead
[   10.546058] cx88[0]/2: frontend initialization failed
[   10.546063] cx88[0]/2: dvb_register failed (err = -22)
[   10.546066] cx88[0]/2: cx8802 probe failed, err = -22
[   10.694016] lp: driver loaded but no devices found

```

---

### Post by viv2 on 2009-05-26
Hi, there was a post saying the firmware in 9.04 was broken. The make sum was wrong  and I am not sure that has been fixed. A work round by getting the correct firmware was posted as below

 				 				**Re: Hauppauge HVR-4000 and mythbuntu: firmware do not load, help** 			
 			 			 		   		 		 		Just had this problem myself with a clean Jaunty x64 install.

The dvb-fe-cx24116.fw firmware file supplied with Jaunty has a md5sum of 9950fe612d47217e6068f7141de225b0. I've replaced with a different firmware file that has a md5sum of 417cafd3b10e207e1dba9a03ad63e405 which seems to work ok.

I got the firmware from
 	Code:
 	wget [ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip](ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip)
unzip -jo 88x_2_119_25023_WHQL.zip Driver88/hcw88bda.sys
dd if=hcw88bda.sys of=/lib/firmware/dvb-fe-cx24116.fw skip=81768 bs=1 count=32522 
Edit: This was using a Nova HD S2 card (detected as Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1)
 		                   		  		  		  		  		 		 			 				 				* 					 						Last edited by Neon Dusk; 3 Weeks Ago at 06:39 PM.. 					 					 				* 			

I had reverted to 8.10 and this works up to a point. 

What I can't get is HDTV BBC or and some of my terrestrial channels eg five are heavily pix-elated and sound breaks are continuous. I know my signal is weaker on these channels but it they all work using Windows and MediaPortal! 

It was a juddery HDTV under Media portal  (Powercinema and Win7 were a disappointment) that prompted me to try linux but so far I am very disappointed with TV under linux. Perhaps as a Newbie, I may not be configuring the Nvidia Geforce 7050/ 630i  and/ or Kaffeine (using xine) or Mplayer (The block pixelation and poor sound occurs with bothplayers) correctly but I have found it difficult to find anything on how to optimise their configurations. 

Sorry this is less than helpful but I though it would be helpful to set out my progress todate.  A reluctant return to Windows beckons.

---

