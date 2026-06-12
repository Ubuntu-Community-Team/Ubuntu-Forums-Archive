---
title: "Mythbuntu 7.10 - Hauppauge WinTV-PVR-500 problems"
date: 2008-03-13
forum: Mythbuntu
---

### Post by cjs500 on 2008-03-13
I have a fresh install of mythbuntu 7.10 amd64 and have a partially working tuner (only one tuner). The second tuner is failing to start. I can't switch between tuners in MythTV using the Y key. It switches to a blank screen and dumps out to the menu.

As far as I can tell it should be supported. Any help on this is greatly appreciated. How can I tell if I have a bad tuner?

Thanks!

This is the dmesg output:

[HTML]
[   29.648580] ivtv:  ==================== START INIT IVTV ====================
[   29.648584] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload ) loading
[   30.700182] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   31.364494] ivtv0: loaded v4l-cx2341x-enc.fw firmware (-139636109703712 bytes)
[   31.582849] ivtv0: Encoder revision: 0x02050032
[   31.582851] ivtv0: Recommended firmware version is 0x02060039.
[   31.641881] tveeprom 1-0050: Hauppauge model 23552, rev E692, serial# 10431054
[   31.641885] tveeprom 1-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   31.641888] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   31.641891] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   31.641894] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   31.641896] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   31.641898] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   31.641901] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   31.659692] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   31.659718] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   31.663454] tuner 1-0060: TEA5767 detected.
[   31.663457] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   31.663469] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   31.663696] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   31.693453] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   34.975228] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   35.068101] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   35.113623] tuner 1-0061: type set to 57 (Philips FQ1236A MK4)
[   35.436663] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   35.436844] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   35.437040] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   35.437123] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   35.437333] ivtv0: Registered device radio0 for encoder radio
[   35.461271] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   35.461343] ivtv:  ======================  NEXT CARD  ======================
[   35.461347] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   36.103846] ivtv1: loaded v4l-cx2341x-enc.fw firmware (-139636109702176 bytes)
[   36.321940] ivtv1: Encoder revision: 0x02050032
[   36.321942] ivtv1: Recommended firmware version is 0x02060039.
[   36.326445] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   36.326457] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   36.329497] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   36.343774] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   36.408406] tveeprom 2-0050: Hauppauge model 23552, rev E692, serial# 10431054
[   36.408409] tveeprom 2-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   36.408412] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   36.408415] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   36.408417] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   36.408420] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   36.408422] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   36.408424] ivtv1: Correcting tveeprom data: no radio present on second unit
[   36.408427] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   36.427351] tuner 2-0061: type set to 57 (Philips FQ1236A MK4)
[   36.427359] ivtv1: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   36.427363] ivtv1: i2c addr 0x44 not found for command 0x4008646f!
[   36.429782] ivtv1: i2c hardware 0x00000001 (cx2584x) not found for command 0x4008646d!
[   36.537675] ivtv1: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   36.537678] ivtv1: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   36.649559] ivtv1: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   36.649606] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   36.649763] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   36.649945] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   36.650022] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   36.652162] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   36.652178] ivtv:  ====================  END INIT IVTV  ====================

[/HTML]

PCI devices:
[HTML]
04:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 500 (1st unit)
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

04:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 500 (2nd unit)
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2
[/HTML]

---

### Post by murbanci on 2008-03-14
Have you made sure that you have the card defined as 2 PVR150 in the backend instead of one tuner?

---

### Post by cjs500 on 2008-03-14
My setup on the backend is the following config:

Probed Info: WinTV PVR 500 (unit #1) [ivtv]
MPEG-2 encoder card (PVR-x50, PVR-500) --> /dev/video0 --> Tuner 1

Probed Info: WinTV PVR 500 (unit #2) [ivtv]
MPEG-2 encoder card (PVR-x50, PVR-500) --> /dev/video1 --> Tuner 1

The options only provide Tuner 1. At first I thought there should be a Tuner 2 but seems this is the way to configure it reference to other posts I've read. Unfortunately this doesn't appear to be working.

---

### Post by BrianH on 2008-03-14
I'm having the same problem.  I just got my PVR-500 and tried to install it today.  My situation looks exactly like yours, except that I also have 2 working PCHD-5500 tuners installed.  I don't know if that makes any difference.

I was wondering if updating the firmware would make any difference.  Mine reports the same as yours below.

[   31.582849] ivtv0: Encoder revision: 0x02050032
[   31.582851] ivtv0: Recommended firmware version is 0x02060039.

I don't have time to try this right now, let me know if you have any luck.

For a workaround I just deleted the /dev/video0 device in the mythtv-setup and I am only using one tuner.

---

### Post by cjs500 on 2008-03-14
I was thinking of the firmware. I'm not exactly sure at the moment where to get it. I did find a reference for a PVR-150 and a link to the FTP site but seems I can't browse the folders on Hauppauge's FTP server for those files for the PVR-500. Does anyone have a link to this?

---

### Post by BrianH on 2008-03-14
> **cjs500 said:**
> I was thinking of the firmware. I'm not exactly sure at the moment where to get it. I did find a reference for a PVR-150 and a link to the FTP site but seems I can't browse the folders on Hauppauge's FTP server for those files for the PVR-500. Does anyone have a link to this?
Maybe this will help...
[http://ivtvdriver.org/index.php/Howto#Firmware](http://ivtvdriver.org/index.php/Howto#Firmware)
[http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)
[http://ivtvdriver.org/index.php/Firmware](http://ivtvdriver.org/index.php/Firmware)

---

### Post by cjs500 on 2008-03-14
Thanks! I just found those as well. I'll update later with the results of how it goes. Hopefully either the firmware file content help or at least be able to create new firmware files using the instructions on the website.

---

### Post by BrianH on 2008-03-15
The new firmware seems to have done the trick.   I have both tuners working now.

All I did was copy these three files...
[INDENT]v4l-cx2341x-dec.fw
v4l-cx2341x-init.mpg
v4l-cx2341x-enc.fw[/INDENT]
from this tar file...
[INDENT][http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)[/INDENT]
into my firmware directory, which on my system was...
[INDENT]/lib/firmware/2.6.22-14-generic[/INDENT]
Then I rebooted and added the cards same as before in mythtv-setup (or if you already have them in there, it should just work)

Good luck, hope yours works too. :)

---

### Post by cjs500 on 2008-03-17
I wasn't so lucky unfortunately. I tried to copy the firmware in the same directory as you did and did see it loaded it but same result with the second tuner issues. 

I ended up trying windows and beyond tv and found the second tuner didn't work also followed by testing for hardware conflicts, moving the card around to different lots, trying it in another machine and all the same so I most likely have a bad card. Off to the computer store tomorrow for a replacement. :(

Thanks everyone for your help!!

---

### Post by cjs500 on 2008-03-27
Figured I'd post a last remark on this thread. I replaced the card and it works now. I didn't have to update firmware. I'll copy in the newer firmware drivers anyway to see if it makes any difference but for now it's all good. 

Also FYI, I tried all sorts of drivers and OS's before returning the card including submitting to hauppauge tech support. I got this link in the reply email from them. Interestingly there where newer drivers not available on the website at the time of this post.

[http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip](http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip)

---

