---
title: "What tuner(s) do you have working in Linux?"
date: 2006-04-08
forum: Multimedia &amp; Video
---

### Post by Donshyoku on 2006-04-08
My previous tuner did not work at all in Linux.  It was identified as a -1 card, according to bttv, that cannot tune a cabel signal.  My current card does not have any audio, as you may know if you've seen some of the threads (and my own) regarding it lately.

So I just wanted to ask, what cards are working?  What cards do you have working in Linux, and do they have a working remote? 

I really want to kick Windows from my HTPC, used almost exclusively for TV, in favor of Ubuntu, but I don't have a working card as of yet.  I've got a bit of money, so hopefully, you can reccomend a good, working (out of the box would be nice, but I don't mind fooling either) Linux tuner!

The cheaper the better, but I really want everything working (tuning, recording) just right.  I can live without a remote, but that would be a huge plus!

Thanks in advance for the help! :)

---

### Post by gitfiddler on 2006-04-12
Donshyoku, I'm gonna give you a bump, because I'm interested in learning the same thing. So far, the posts and the how-to's in this forum seem to point to the Hauppauge cards as being the best supported and easiest to set up. The PVR-350 is about $150(US), and is the one I've set my sights on, but I haven't tried it yet.
Let's hope someone posts more info here.

---

### Post by Cal Little on 2006-05-18
My research has led me to the pcHDTV card at [http://pchdtv.com](http://pchdtv.com). This is a fully compliant linux card with support for NTSC analog, ATSC over the air HDTV  and all of the standards for QAM unencrypted cable digital signals. It is designed to work with MythTV.  I just checked the site this morning and the latest version has just been released for $130. I have been waiting a month since they have been out of stock of the previous model. The reviews are very promising and I will be adding this to my box in the near future. Good luck on the tv project.

---

### Post by richbarna on 2006-05-18
[QUOTE=gitfiddler]Donshyoku, I'm gonna give you a bump, because I'm interested in learning the same thing. So far, the posts and the how-to's in this forum seem to point to the Hauppauge cards as being the best supported and easiest to set up. The PVR-350 is about $150(US), and is the one I've set my sights on, but I haven't tried it yet.
Let's hope someone posts more info here.[/QUOTE]

Hi fellow TV viewers, 
I am using a Hauppauge WinTV Express card with KdeTv and it works sweet.
I live in Spain and the TV card cost me 50 euros, $'s I don't know.

The only thing is, if you use a web cam, there are conflicts.
I am currently trying to solve this problem, however the forums are full of such complaints, but not many solutions at the moment.

---

### Post by dlai on 2006-05-20
I've got the pvr-150 going with xawtv on my box...

---

### Post by gitfiddler on 2006-05-22
Cal Little,

Thanks for the info. *If* it works, it could be the perfect solution. 

(One note: There is no hardware encoder or decoder on this card, it relies on software, creating a greater hit on the system. Not best suited for systems running in the 1.0 - 1.8 Ghz range)

Does anyone have this card working with Ubuntu?

---

### Post by Vincent_Lin on 2006-06-20
Has anyone got Kworld atsc-110 to work in ubuntu at all?  

Unfortunately I saw in linuxtv.org that thid card is not "supported" yet,  even though it seems that all the components of this card are supported individually.  saa7133, bt798(?), cx88, etc...

Thanks.

Vincent

PS, "unfortunately" means I have this card, but I could not get it to work with Dapper, not to mention mythtv.

---

### Post by Vincent_Lin on 2006-06-24
Hi,

Just to report the progress:

My Kworld atsc-110 is now recognized by saa7134 driver, using card=90 tuner=68.  it is an extremely long trial and error process since /usr/src/linux/Documentation/vidoe4linux/CARDLIST.saa7134 only documents card number up to 82.  Who knows there is another card=90 hanging up there.  I only spotted the dmesg output by accident while I was trying card=75, and saa7134 driver, somehow, auto-detects it as card=90 atsc-110.

I installed Mercurial and use the command 

  hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) 

and compiled v4l drivers from it.

My question:

Even though saa7134, when loaded with proper card and tuner parameter, recognizes this card, saa7134-dvb, after loading nxt2004 firmware, would mis-recognize this card to be something like Nextwave NXT200X VSB/QAM frontend, and no any further action I can achieve.  I tried dvb-apps with the utility scan using us-MA-Boston, but none chennel was locked and recognized.  mythtv complains nextwave nxt200x vsb/qam is no good at all.

Furthermore, while I can force mythtv to scan chennels using this frontend, nxt200x firmware/driver complains like this
552.656000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185552.760000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185552.864000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185552.972000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185553.076000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185553.180000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185553.284000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185553.388000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185553.492000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185553.596000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5)
[17185553.700000] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -5).
..........................................

Could someone help?  I did not use ivtv at all.  Would that be the matter?  Why saa7134-dvb could not recognize this card, while saa7134 could?  What other steps I can try from here?

Thanks in advance,

Vincent

---

### Post by MonkeyNet on 2006-06-24
I am using both a WinFast TV 2000 XP Expert edition and a Hauppauge PVR-150MCE

Both cards work great. Having some issues with the remote but working on that as we speak :)

---

### Post by cblanquer on 2006-06-25
Hi,

Mine is Asus My Cinema "ASUSTeK P7131 Dual". I chose it because it was one of the 1st available allowing to choose analog or digital signals and also caturing analog input.

No very satisfactory under windows as the analog sound sucks, probably as no direct analog plug to the board is provided, which does not allow good recordings from my sat box nor VHS tapes. The provided application to drive it is really too much resource consumming and too slow.:( 

In Linux I have not been able to proper configure "ivtv" yet for it. I can make it run and get video on TVTime, for sound I must run a command to redirect digitally captured sound, which results in a perceptible delay !
Finally I found little info on forums regarding that card, I am currently expecting some feed-back from somebody who said he made it work with MythTV.](*,) 
Good luck.

============================
[17179590.228000] Linux video capture interface: v1.00
[17179590.284000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179590.284000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179590.284000] saa7133[0]: found at 0000:02:0c.0, rev: 208, irq: 201, latency : 32, mmio: 0xfeaff000
[17179590.284000] saa7133[0]: subsystem: 1043:4862, board: ASUSTeK P7131 Dual [c ard=78,autodetected]
[17179590.284000] saa7133[0]: board init: gpio is 0
[17179590.420000] saa7133[0]: i2c eeprom 00: 43 10 62 48 54 20 1c 00 43 43 a9 1c  55 d2 b2 92
[17179590.420000] saa7133[0]: i2c eeprom 10: 00 01 20 00 ff 20 ff ff ff ff ff ff  ff ff ff ff
[17179590.420000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d6  ff ff ff ff
[17179590.420000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff  ff ff ff ff
[17179590.420000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 00 ff ff  ff ff ff ff
[17179590.420000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff  ff ff ff ff
[17179590.420000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff  ff ff ff ff
[17179590.420000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff  ff ff ff ff
[17179590.424000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Chan nel
[17179590.424000] rt2500 EEPROM: 17 17 17 17 16 16 16 16 16 17 17 17 17 17  dBm Maximum
[17179590.448000] saa7133[0]: registered device video0 [v4l2]
[17179590.448000] saa7133[0]: registered device vbi0
[17179590.448000] saa7133[0]: registered device radio0
[17179590.460000] saa7134 ALSA driver for DMA sound loaded
[17179590.460000] saa7133[0]/alsa: saa7133[0] at 0xfeaff000 irq 201 registered a s card -1
[17179590.824000] lp: driver loaded but no devices found

============================

---

### Post by kraz on 2006-06-25
PVR-150 MCE took some time for me as a totally new linux user to set up, but now I have mythtv working flawlessly on my desktop, in a window, recording what I want to see, etc. Didnt try xawtv as it seems I would need to compile the new version for it to work, but MythTV meets my need, so I think I will stick with that.

Only thing Id say you require is a lot of patience for it to work. trials and errors, and.. the .44 drivers, since others seem to not work.

I read most of the guides and tried them out, and after 4-5 hours I had a moving picture, sound, etc. Channels, I had to add manually from a danish listing, but I can download the program listings and plan recordings from them now. Took a little time, but was worth the effort.

If you ever get as far as to see a picture in mythtv, but you get stuck at your pc locking up when changing channels, remember to bind mysql to another IP than 127.0.0.1 Helped me.

BTW: I have a pinnacle PCTV-USB2 card also, and I have got it to work in ubuntu, since its detectable by the system now. But It wasnt able to show all channels from my cable-provider, and I never found out why. So I had to have an XP partition ready for that to work 100%.

---

### Post by cblanquer on 2006-06-26
To complete my former post:
I discovered yesterday night my card s  not supposed to run ivtv but rather another driver.
[http://linuxtv.org/v4lwiki/index.php/Saa7134_devices_%28saa713x%29](http://linuxtv.org/v4lwiki/index.php/Saa7134_devices_%28saa713x%29)

So I would rather advice to spend some hours reading in linuxtv.org...

---

### Post by pump on 2006-07-02
Does anybody have a Pinnacle PCTV Stereo running under Ubuntu?

---

### Post by Bezmotivnik on 2006-07-18
I just got a KWorld PVR TVR300-U for free after rebate, but it's never even crossed my mind to try it under Ubuntu.

Is there even a **chance** that these USB TVR devices would work under Linux? :confused:

---

### Post by nomats on 2006-07-20
Hay fellow members!

I'm going to buy a USB digital tv card for my laptop. I've set my eyes on Hauppauge's WinTV-NOVA-T-Stick. I checked out linuxtv.org's wiki but didn't find the card there. I did find out though that it's based on DibCom7700 chipset. Does anyone know if there is support coming for it or should I buy the bit more expensive NOVA-T-USB2 which is already supported? I'm not sure whether I want to pay ~30 euros for a remote control that I probably don't even need.

---

### Post by phenolholic on 2006-08-09
Hello,
I have a KWorld KW-878RF-PRO (card=78) and it doesn't seem to work. In tvtime, I get a fuzzy scrammbled-like picture. I know it's receiving the signal because when I change the channels, I can tell the channels are indeed changing but can't seem to get rid of the fuzz to make a clear picture. Can anyone outline the steps from initial to getting popcorn to watch TV just to reassure myself I didn't miss a step? Thanks in advance!

---

### Post by fut21 on 2006-08-09
Cinergy 1400 DVB-T works out of the box. I use kaffeine and everything works.
The remote-control works particaly out of the box.

---

### Post by darkteckno on 2006-09-20
Try Asking here: [http://tech.groups.yahoo.com/group/KWORLD-TV/](http://tech.groups.yahoo.com/group/KWORLD-TV/)

---

