---
title: "Leadtek WinFast HDTV Cinema"
date: 2008-08-09
forum: Multimedia Software
---

### Post by yojimba on 2008-08-09
Starting a thread for support of this card. 

Card is listed on LinuxTVWiki as : "likely work as is or can be made to work with some manual configuration" and "similar to the KWorld ATSC 110" 

[http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards](http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards)

[http://marc.info/?l=linux-dvb&m=119747668120799&w=2](http://marc.info/?l=linux-dvb&m=119747668120799&w=2)

Someone installed this card as if it were the kworld 110 and it "works great" without remote support.

[http://marc.info/?l=linux-dvb&m=119894770924594&w=2](http://marc.info/?l=linux-dvb&m=119894770924594&w=2)

The card has a nice price right now from New Egg with a mail in rebate . . . I'm sure there will be interest. I'm going to purchase and give it a go hoping to get it running with Mythbuntu. . . thought others might be interested.

---

### Post by yojimba on 2008-08-13
Hoping to get some help with the above project:

The card is now in the case but is recognized within MythTV as an "unknown card". How do I go about installing the card as a KWorld ATSC 110 per this suggestion:

[http://marc.info/?l=linux-dvb&m=119894770924594&w=2](http://marc.info/?l=linux-dvb&m=119894770924594&w=2)

I assume I have to get the driver from KWorld, install it manually and link it to the card. Any recommendations on how I would go about doing that? I'm not sure what to Google to even find out.

---

### Post by yojimba on 2008-08-14
After further digging around I've found more detailed instructions for making the card work as the KWORLD ATSC 110:

[http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_HDTV_Cinema](http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_HDTV_Cinema)

Wish me luck! And please post the results of your own efforts.

---

### Post by yojimba on 2008-08-16
I'm at a road block.

I have added the the necessary nxt2004 firmware to what should be the proper directory /lib/firmware/[kernal version] (which in my case is /lib/firmware/2.6.24-19-generic)

I have also added the following to modprobe.conf:

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=90 '
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

After reboot, the card should now be recognized as the KWORLD ATSC 110. However, when running dmesg, it is still seen 'unkown". 

The firmware should be in the correct directory . . . so I'm figuring the problem is in the modprobe.conf file.

Here is the modprobe.conf file. Maybe there are conflicts between the added lines and the bttv entry? Or is there something I have done incorrectly in adding the lines above? (I did take out the " after 'card-90' as it looked like a typo).


>>>>>>>>>>>>>>>>>>>>>

# i2c
alias char-major-89	i2c-dev
options i2c-core	i2c_debug=1
options i2c-algo-bit	bit_test=1

# bttv
alias char-major-81	videodev
alias char-major-81-0	bttv
options	bttv		card=2 radio=1
options	tuner		debug=1

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=90

>>>>>>>>>>>>>>>>>>>>>>>>>>

---

### Post by yojimba on 2008-08-18
bump . . . 

i believe there might be a conflict here between bttv and saa7134 . . . as they are drivers for two different chipsets . . . 

i didn't add the bttv lines . . . is the system detecting the card with a bttv chip?

i'm swimming pretty deep here . . . any help out there? this has been a great way to learn and i'd really like to help get this tuner on the compatible mythtv hardware list.

---

### Post by Nicholi on 2009-04-13
Any solution on this?

---

### Post by STYX2009 on 2009-06-02
You can download the v4l-dvb driver for Leadtek HDTV Cinema here:
[http://tw1965.myweb.hinet.net/Linux/v4l-dvb/20090617-HDTV200H/v4l-dvb.tar.gz](http://tw1965.myweb.hinet.net/Linux/v4l-dvb/20090617-HDTV200H/v4l-dvb.tar.gz)
[http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/)

 
The tvtime works with HDTV Cinema for analog TV.
 
The dvb-fe-nxt2004.fw is needed for digital TV (ATSC, QAM).
And you can find the dvb-fe-nxt2004.fw in the following compression file:
[http://tw1965.myweb.hinet.net/Linux/firmware.tar.gz](http://tw1965.myweb.hinet.net/Linux/firmware.tar.gz)

---

### Post by jasonhoekstra on 2009-10-13
I was able to get this to work, it took a lot of searching and hacking, but eventually this can work (confirmed both analog and digital).

---

