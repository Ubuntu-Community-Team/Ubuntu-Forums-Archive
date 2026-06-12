---
title: "Hauppauge PVR 350 - Ubuntu 7.10"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by abrand1972 on 2007-10-27
Hi,

I have just installed Ubuntu 7.10. Everything works just great - but I am a NewBe.

I only have trouble with my Hauppauge PVR 350 card. Regardless of which TV viewer program (kaffeine, XWATV, TvTime, MythTV, ...) I use, it does not work.

Is there anything I forgot? 
Like installind drivers?

Does astep-bystep instruction exist, how to get this to work?

Thanks for the help
Alex

---

### Post by abrand1972 on 2007-10-27
any ideas?

---

### Post by paulmac on 2007-10-27
I sure hope you get a good answer.  I'd love to use Gutsy as my HTPC  but am afraid to try it.  My xp box is doing ok but the more I play with linux, the more I want it  for HTPC.  I sure hope the  driver support for graphics and capture cards can continue to mature.

---

### Post by abrand1972 on 2007-10-29
this is exactly what I want ... it works nicely under Win XP - but I rather use Ubuntu ... hope someone can help on this

---

### Post by Ubuntwan on 2007-10-29
in this forum there are many posts about the hauppauge tuner cards, so with some searching there should be tons of info. But I can see it may be difficult to know where to look or what to look for. Lets see if your card is installed properly: could you show the output of the  **dmesg** command  between the lines "======== START INIT IVTV ==========" and  "======== END INIT IVTV ==========" and also the output of **ls /dev/video*** ? This will give a good starting point to find out why it is not working

---

### Post by abrand1972 on 2007-10-30
dmesg gives me
"[   39.013633] ivtv:  ==================== START INIT IVTV ====================
[   39.013638] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   39.013752] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   39.013816] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 20
[   39.034718] 
[   39.034720] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[   39.034724] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   39.039052] lirc_dev: lirc_register_plugin: sample_rate: 0
[   39.061210] lirc_atiusb[3]: X10 Wireless Technology Inc USB Receiver on usb1:3
[   39.087841] usbcore: registered new interface driver lirc_atiusb
[   39.132905] usbcore: registered new interface driver ati_remote
[   39.132912] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/misc/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
[   39.651853] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   39.757014] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4157061136 bytes)
[   39.799651] ivtv0: loaded v4l-cx2341x-dec.fw firmware (4157061144 bytes)
[   40.021567] ivtv0: Encoder revision: 0x02050032
[   40.021570] ivtv0: Recommended firmware version is 0x02060039.
[   40.029567] ivtv0: Decoder revision: 0x02020023
[   40.093624] tveeprom 0-0050: Hauppauge model 48134, rev J347, serial# 6596620
[   40.093629] tveeprom 0-0050: tuner model is LG TP18PSB01D (idx 47, type 28)
[   40.093632] tveeprom 0-0050: TV standards PAL(B/G) (eeprom 0x04)
[   40.093634] tveeprom 0-0050: audio processor is MSP4418 (idx 25)
[   40.093637] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   40.093639] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   40.093643] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   40.124859] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   40.186838] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   40.362008] saa7127 0-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[   40.389566] msp3400 0-0040: MSP4418G-A2 found @ 0x80 (ivtv i2c driver #0)
[   40.389571] msp3400 0-0040: MSP4418G-A2 supports nicam and radio, mode is autodetect and autoselect
[   40.389800] tuner 0-0061: type set to 28 (LG PAL_BG+FM (TPI8PSB01D))
[   40.663774] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   40.664037] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   40.664272] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   40.664388] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   40.664653] ivtv0: Registered device radio0 for encoder radio
[   40.664723] ivtv0: Registered device video16 for decoder MPEG (1 MB)
[   40.664825] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
[   40.665168] ivtv0: Registered device vbi16 for decoder VOUT
[   40.665239] ivtv0: Registered device video48 for decoder YUV (1 MB)
[   40.717107] ivtv0: loaded v4l-cx2341x-init.mpg firmware (4157062448 bytes)
[   40.927442] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[   40.927477] ivtv:  ====================  END INIT IVTV  ===================="

ls /dev/video says:
/dev/video0  /dev/video16  /dev/video24  /dev/video32  /dev/video48


What does that tell me?

Thanks
Alex

---

### Post by Ubuntwan on 2007-10-30
this tells you that the card is detected and installed properly: You can see that firmware is loaded and that devices have been created in the /dev directory. /dev/video0 is the mpeg tuner you are looking for.
So the programs you use should point at this device. I dont use the programs you tried (although they should work) but use vlc. Perhaps you can install vlc so i can tell you a little bit more (i'm not very experienced either)
The cards input needs to be selected (the cable or the S-Video, etc) and in case of the cable input the card has to be tuned to a certain frequency. The whole thing with channels only works if you have the correct channel-map. My tv provider has shifted away from the northern-european channel map so i have to hand pick them (I haven't found out how to create my own channel map).

So everything looks ok so far.
Find out a frequency for a channel of your local tv provider. tune the card to the correct input and frequency usng ivtv-tune (maybe you have to install this as well)
**ivtv-tune -f 219 ** sets the tuner to 219 MHz (a used frequency in my area) 
install vlc and choose file -> open capture device -> PVR and choose the correct device (/dev/video0 in your case) If the wrong input is chosen i do not know how to set it in vlc. I use mencoder (comes with mplayer) to record video (and convert on the fly to put on my zen vision m) and that has some method to set everything in the correct way after which vlc uses these settings.
 mencoder pvr:// -tv driver=v4l2:device=/dev/video1:norm=pal:input=2:fps=25:width=640:height=480 -ovc xvid -oac copy -ofps 25 -xvidencopts bitrate=1500 -vf softskip,format=yv12,scale=320:240 -o outfile.avi
(all on one line) This sets my tuner to /dev/video1 (my webcam sits on /dev/video0) and the input to 2 which is the s-video input to which i have connected my digital set top box tv tuner provided by the cable company.

So try vlc first, and if it doesn't work try to set the input to 1 (i think) with the mplayer command (use ctrl C to stopt he recording of mplayer)

I know this is not a nice way to use the card, but at least it may show you that it does work and then you can find other ways and programs to use it properly

please tell the outcome of all this

---

### Post by Peque on 2007-10-30
Normally this is not a problem using Hauppauge tuners along with those programs as you name. I haven't had any problems using MythTV with an Hauppauge PVR500. 

But the tricky part is properly that you're not aware of the change to /dev/video0 which (normally from MythTV) should be as easy as possible to set up - from MythTVsetup !

---

