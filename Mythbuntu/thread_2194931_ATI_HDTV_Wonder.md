---
title: "ATI HDTV Wonder"
date: 2013-12-21
forum: Mythbuntu
---

### Post by Senkoboy on 2013-12-21
Will this card, ATI HDTV Wonder, still work with Mythbuntu 12.04.  I am looking to upgrade from 10.04, new install and want to make sure it will still work. 

Thanks

---

### Post by novellahub on 2013-12-23
> **Senkoboy said:**
> Will this card, ATI HDTV Wonder, still work with Mythbuntu 12.04.  I am looking to upgrade from 10.04, new install and want to make sure it will still work. 

Thanks

Yes.  I have 3 of them in my Mythbuntu 12.04 setup running Mythtv 0.27.  Just make sure you have the firmware in /lib/firmware

[http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder](http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder)

---

### Post by Senkoboy on 2013-12-24
I have 2 of the  ATI HDTV wonder cards that are working in my old setup, Lucid running myth .22, since upgraded to .25.   I remember it was a pain for me to get them running last time.   I have tried to install the firmware a couple of different ways with out success.  When I tried to do it from [http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmwarehttp://]("http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmwarehttp://") I got

 > mike@mike-desktop:~$ cd /usr/share/doc/dvb
mike@mike-desktop:/usr/share/doc/dvb$ sudo chmod +x ./get_dvb_firmware
[sudo] password for mike: 
mike@mike-desktop:/usr/share/doc/dvb$ sudo ./get_dvb_firmware nxt2004
--2013-12-24 10:03:03--  [http://www.avermedia-usa.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip](http://www.avermedia-usa.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip)
Resolving [www.avermedia-usa.com](www.avermedia-usa.com) ([www.avermedia-usa.com](www.avermedia-usa.com))... 66.85.153.58
Connecting to [www.avermedia-usa.com](www.avermedia-usa.com) ([www.avermedia-usa.com)|66.85.153.58|:80](www.avermedia-usa.com)|66.85.153.58|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-12-24 10:03:06 ERROR 404: Not Found.

wget failed - unable to download firmware at ./get_dvb_firmware line 829.
mike@mike-desktop:/usr/share/doc/dvb$ 


I also tried the instructions from [http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder]("http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder") had problems there also.

# cd /[kernel source directory]/Documentation/dvb/
# perl get_dvb_firmware nxt2004

My kernel is 3.8.0-34, but the dvb folder is not there. 

I also went to [http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTVHD_MCE_A180]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTVHD_MCE_A180")

I did end up with a zip file called AVerTVHD_MCE_A180_Drv_v1.2.2.16, but is a 0 byte file.

I am not sure what I need to do to get this working?  I can't even find the /lib/firmware file.

I did find a copy of the firmware (Dvb-fe-nxt2004.fw.zip) here [http://ubuntuforums.org/showthread.php?t=1696935http://]("http://ubuntuforums.org/showthread.php?t=1696935http://")

I guess I need to know what to try next?

Thanks

---

### Post by Senkoboy on 2013-12-24
I might have it, scanning now.  Will post more later

---

### Post by Senkoboy on 2013-12-24
Ok, I found a page [http://pyther.net/2012/07/nxt2004-firmware/]("http://pyther.net/2012/07/nxt2004-firmware/")


To Install:

    wget [http://pyther.net/files/firmware/nxt2004/dvb-fe-nxt2004.fw](http://pyther.net/files/firmware/nxt2004/dvb-fe-nxt2004.fw)
    cp dvb-fe-nxt2004.fw /lib/firmware
    reboot
    check out dmesg to confirm firmware was loaded

It worked, channel scan picked up my channels.  I still have problems with my backend, but that is a different story.

I got this when I ran dmesg

> [    3.302240] DVB: registering new adapter (cx88[0])
[    3.302244] cx88-mpeg driver manager 0000:07:00.2: DVB: registering adapter 0 frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[    3.302782] cx88[1]/2: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34]
[    3.302786] cx88[1]/2: cx2388x based DVB/ATSC card
[    3.302788] cx8802_alloc_frontends() allocating 1 frontend(s)
[    3.304102] nxt200x: NXT2004 Detected
[    3.304936] tuner-simple 2-0061: creating new instance
[    3.304939] tuner-simple 2-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[    3.304942] DVB: registering new adapter (cx88[1])
[    3.304946] cx88-mpeg driver manager 0000:07:02.2: DVB: registering adapter 1 frontend 0 (Nextwave NXT200X VSB/QAM frontend)...



Thanks

---

### Post by novellahub on 2013-12-26
Glad you got it working. I keep a backup of the firmware separately when upgrading to a new install.

---

### Post by Phuriousgeorge on 2014-03-01
Hello, this thread seemed to be exactly what I needed.

I've got an [ADS PVT-382-525]("http://www.linuxtv.org/wiki/index.php/ADS_Tech_Instant_HDTV_PCI"), which seems to have mostly the same hw as your [HDTV Wonder]("http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder"). I attempted the fix posted from [http://pyther.net/2012/7/nxt2004-firmware/](http://pyther.net/2012/7/nxt2004-firmware/), but seem to be having issues. I atried dmesg and seems to be the same issue listed here: [https://lists.ubuntu.com/archives/kernel-team/2014-January/037708.html](https://lists.ubuntu.com/archives/kernel-team/2014-January/037708.html).
  
Anyone know of a solution? Be gentle, this is my 1st desktop Linux build, so I'm not so great at troubleshooting just yet ;)

Running 12.04 LTS

EDIT: Just noticed the [SOLVED]...I'll create my own thread: [http://ubuntuforums.org/showthread.php?t=2208721&p=12944102#post12944102](http://ubuntuforums.org/showthread.php?t=2208721&p=12944102#post12944102)

---

### Post by sdowney717 on 2014-03-03
How well does this card work with HDTV, any stutters?
How well will it work with a pentium 3 ghz geforce 6200 agp PC?

This PC does play 1080p ok in smplayer or vlc. 
But I have to leave deinterlacing off, or the video slows down

---

