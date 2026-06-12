---
title: "I only get static on my PVR-250"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by jaw1959 on 2007-06-18
I'm trying to setup my PVR-250 to work with mythtv, and when I test the card, all I get is static. I'm using "cat /dev/video0 > test.mpg" to test the card.  Everything I can check to see if the card is working seems to indicate that it is setup correctly, but I can't make it display anything but static.  When I change the channels I can make the static look slightly different, but that's all I can seem to do.  Also, there is on audio no my test recordings.  Any ideas?

I just installed the ivtv-firmware package from the ubuntu repositories (version .20070217) which did not seem to change anything.  

Thanks for any help

Josh

---

### Post by jaw1959 on 2007-06-19
Here is a question I submitted to the ivtv mailing list:

I have a PVR-250 that I bought in the fall of 2002.  I recently started trying to setup MythTV on an Ubuntu Feisty Fawn box with the intention of using this card.  I haven't used the card in years, so I'm not 100% sure the hardware works.  When I try to test the card with VLC or "cat /dev/video0 > /media/disk/store/Media/Video/Recordings/test.mpg" all I get is static.  There is no sound on the test recordings either.  I downloaded the firmware from the Ubuntu repositories and installed it with synaptic package manager, but that didnt seem to change anything.  When I try changing the channels (I'm using standard analog cable as the source) I can get slight variations in the static I see, but other than that, I see no change.  I believe the firmware version is .2007217. 

I'm not really experienced with this type of thing, and I'm fairly new to Linux, so please let me  know if there is something I can do to provide better information to help diagnose the problem.  I've found various "how-to" procedures to troubleshoot the problem, and every indication I can find seems to suggest the card is correctly identified by the machine and I haven't seen any errors.  Here's a few things I've tried and the output I've seen:

root@Dell-8200:/media/disk/store/Media/Video/Recordings# dmesg |grep Initialized[   34.185184] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
root@Dell-8200:/media/disk/store/Media/Video/Recordings# dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
[   32.305558] ivtv:  ==================== START INIT IVTV ====================
[   32.305563] ivtv:  version 0.10.1 (tagged release) loading
[   32.305565] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586
[   32.305567] ivtv:  In case of problems please include the debug info between
[   32.305569] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   32.305571] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   32.305678] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   32.305734] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 20
[   32.322730] usbcore: registered new interface driver libusual
[   33.041592] ivtv0: loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   33.137892] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   33.360552] ivtv0: Encoder revision: 0x02060039
[   33.368531 ] ivtv0: Decoder revision: 0x02020023
[   33.439574] tveeprom 0-0050: Hauppauge model 48012, rev G310, serial# 2600481
[   33.439579] tveeprom 0-0050: tuner model is Philips FI1236 MK2 (idx 10, type 2)
[   33.439582 ] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   33.439584] tveeprom 0-0050: audio processor is MSP3445 (idx 12)
[   33.439586] tveeprom 0-0050: has radio
[   33.439589] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   33.467337] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   33.552178] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   33.763020] msp3400 0-0040: MSP3445G-B8 found @ 0x80 (ivtv i2c driver #0)
[   33.763024] msp3400 0-0040: MSP3445G-B8 supports radio, mode is autodetect and autoselect
[   33.764738] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   33.764954] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   33.765196] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   33.765298] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   33.765559] ivtv0: Registered device radio0 for encoder radio
[   33.765581] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   34.185184] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
[   34.185206] ivtv:  ====================  END INIT IVTV  ====================

Any assistance in this matter would be greatly appreciated. 

Thanks,

Josh

---

### Post by tlianza on 2007-06-26
I'm in a similar boat with my 350, but I was able to get video if I use the "ivtv-tune" utility and then do a test capture.  For example:

$ ivtv-tune -c13
/dev/video0: 211.250 MHz  (Signal Detected)

Then do a test capture and I get video and audio.  This made me think that it's mythtv that's screwing up, because it is only capturing static.  Do you see the same behavior?

---

### Post by tlianza on 2007-06-27
Aha... I figured my problem out, but I'm not sure if it was the same as yours.

As it turns out, I was getting channels under 13 ok, but no UHF channels.

I just had to run mythtv-setup, and change the "channel frequency table" from us-bcast to us-cable and everything worked fine after that.  Oops!  Hope this helps someone.

---

