---
title: "Hauppage DVB-T cards and Karmic - a solution"
date: 2010-03-07
forum: Multimedia Software
---

### Post by coffeecat on 2010-03-07
Actually, just one particular Hauppage card - a Hauppage WinTV Nova TV-500 (I think - the packaging is lost). There are various versions with this model number. Mine has (from lspci):

> 01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)... and me-tv identifies it as: "Philips TDA 10046H DVB-T"

It worked fine in Jaunty but doesn't in a default install of Karmic. It occurred to me that the firmware was missing because there are only two dvb* files in the Karmic /lib/firmware, whereas there are 21 in the Jaunty /lib/firmware. So I simply copied all the 21 dvb* files from Jaunty into the Karmic /lib/firmware, rebooted and the card now works. Clearly, I only need one of those files, but life is short and I have neither the time nor the inclination to sort out specifically which is needed. I simply offer this crude fix for others with the same Philips/Hauppage. Or any other make with the same Philips chipset.

As a backup I've copied the 21 firmware files to my archives, and as a double backup I'll make sure I keep the Jaunty live CD (and ISO) handy for as long as I need them. (You can get the dvb* files from the live session if need be.)

I'm not asking for any support, but comments are welcome. In particular, does anyone know why the firmware for this device (and others judging by the dearth of dvb* files in a default Karmic install) is missing? I bought Hauppage because, at the time, it was said to be the most Linux-friendly make of DVB-T cards.

---

### Post by coffeecat on 2010-03-07
> **coffeecat said:**
> crude fix

....

In particular, does anyone know why the firmware for this device (and others judging by the dearth of dvb* files in a default Karmic install) is missing?

Ho hum - I should have realised it would have to be about nonfree stuff. (What's the matter with these manufacturers? Don't they want us to use their products?) The less crude fix is to install the package linux-firmware-nonfree. As I've just discovered. :roll:

---

### Post by natrixnatrix89 on 2010-03-07
Hi. I have a TV tuner too.
it is: 
```
05:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```
I'm running karmic, but I have no idea, how to run it. What is the appropriate application to watch tv? And how can I switch channels?

---

### Post by coffeecat on 2010-03-08
Probably the easiest way to get started is to use the application me-tv. Make sure you've installed the package linux-firmware-nonfree before you run me-tv. If my experience is anything to go by, the Philips dvb chip sort-of works without the firmware so that me-tv doesn't give you a 'device not found' type error, but when you do a channels scan it doesn't find anything. So install the firmware package first and then reboot before running me-tv for the first time.

When first run, me-tv needs to scan for channels to create a database. It presents you with a wizard with two initial choices. The first is "Scan using an initial scan file". Click on the dropdown box and choose the file appropriate to your transmitter - you have to know this. (I've had a look - I should imagine the "lv-Riga" one would be yours.) Then complete the scan. Or, if you have an appropriate channels.conf file, you can use this instead for the second choice. The channels.conf must be specific to your transmitter and this choice is really only for those who've already set up their TV tuner and have a channels.conf edited to their liking. (You can find channels.conf files on the internet, but in my experience they're hopelessly out of date.)

Once you've got me-tv set up it's easy to use. Changing channels is just a mouse click. There are other tv-tuner apps - just search Synaptic.

You may hear about Mythbuntu. Don't go there just yet - not with that card. Myth-TV is a very sophisticated home TV set of apps, and Mythbuntu is an Ubuntu variant specifically for running MythTV. **There is a major problem with this Philips chip** and MythTV. You install Mythbuntu from a live CD just like Ubuntu, but then you have to do the initial set up of MythTV from the live CD (which includes a channels scan) before you reboot into the hard disk install of MythTV. But without the firmware in the default install I couldn't do a successful channels scan and complete the initial setup. And when I tried to reboot to do the setup from inside the installed Mythbuntu, it failed to launch the desktop with a flashing screen and an error that suggested the problem was in the incomplete initial setup.

I'm working on it. I can't believe there isn't a workaround.

---

### Post by natrixnatrix89 on 2010-03-09
Wow! This was very helpful! Thank You.
I was searching for the appropriate application for this, but had no luck.
Yes. And I tried the mythtv-backend on my computer, but it didnt really work out and I couldnt configure the channels. And also I noticed that everytime I try to shut down I got a password prompt because "other users are logged in". Turned out that was mythtv. Once I purged it I dint have that problem anymore.
Ok I'll try this me-tv
Thank you very much!

---

### Post by Chronon on 2010-03-09
Thanks.  This helped me too.

---

### Post by natrixnatrix89 on 2010-03-09
A little problem:
I had nonfree drivers already installed:
> linux-firmware-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

But when I run me-tv, I get this error:
[IMG]http://jaunciema-osta.lv/error.png[/IMG]
When I was looking for the software I installed tvtime. I didnt know how to use it and all i could see was a black screen. Now that I have upgraded to Karmic, It says there is no device too. So I can assume the device worked before I upgraded :/ 
[IMG]http://jaunciema-osta.lv/error2.png[/IMG]

---

### Post by natrixnatrix89 on 2010-03-09
Hmm. This is interesting: > jancis@jancis-pc:~$ tail -f /dev/video0
tail: error reading `/dev/video0': No such device
tail: `/dev/video0' has become accessible
tail: /dev/video0: cannot seek to offset 0: Illegal seek

And there has appeared another device /dev/video1

---

### Post by coffeecat on 2010-03-09
> **natrixnatrix89 said:**
> Now that I have upgraded to Karmic, It says there is no device too. So I can assume the device worked before I upgraded :/

I see - you did an upgrade to Karmic, not a fresh install. That might explain why the nonfree firmware was already in place. It seems that the nonfree package was part of a default Jaunty but not of a default Karmic, but when you did the dist-upgrade, the firmware would have remained in situ. Apart from that I can't help. All I can say is that the kernel driver in Karmic works on my card and you have the correct firmware.

**Edit:**: just had a thought.

Me-tv is a bit odd. When you open it a blue icon appears in the upper  panel to the right. You have to close down me-tv with this icon. If you  simply close the me-tv window with the close button, the me-tv process  continues running. If you then go to the menu to open it again, you open a second me-tv process and you get a "device not found" error. Make sure you have all instances of me-tv closed properly. That one has caught me out on more than one occasion.

**Edit2:** I have no experience of tvtime, but an alternative to me-tv is Klear. It's a KDE app so it will bring in some KDE libraries, but I seem to remember that it worked well enough.

---

### Post by natrixnatrix89 on 2010-03-09
Maybe a driver is missing?
but after dmesg I can see:
> jancis@jancis-pc:~$ dmesg | grep saa7133
[   26.435021] saa7133[0]: found at 0000:05:01.0, rev: 209, irq: 19, latency: 32, mmio: 0xf8109000
[   26.435028] saa7133[0]: subsystem: 1461:2c00, board: UNKNOWN/GENERIC [card=0,autodetected]
[   26.435042] saa7133[0]: board init: gpio is 2b600
[   26.435047] IRQ 19/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   26.606408] saa7133[0]: i2c eeprom 00: 61 14 00 2c 00 00 00 00 00 00 00 00 00 00 00 00
[   26.606422] saa7133[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   26.606434] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 03 01 08 ff 00 a3 ff ff ff ff
[   26.606446] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606458] saa7133[0]: i2c eeprom 40: ff 32 00 c0 86 1e ff ff ff ff ff ff ff ff ff ff
[   26.606470] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606482] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606494] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606506] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606518] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606530] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606542] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606554] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606566] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606579] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.606590] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.607553] saa7133[0]: registered device video1 [v4l2]
[   26.607580] saa7133[0]: registered device vbi0
[   27.191841] IRQ 19/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   27.191864] saa7133[0]/alsa: saa7133[0] at 0xf8109000 irq 19 registered as card -2


And Yes. It wasn't related to the problem you mentioned that me-tv would already be running. There was no notification icon there before I run me-tv.

Should I search for the driver? Or is it related to something else?

---

