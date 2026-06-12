---
title: "Ati driver installiation: Toshiba Satellite A105"
date: 2006-02-27
forum: Multimedia &amp; Video
---

### Post by k5knt on 2006-02-27
**Ati driver installation: Toshiba Satellite A105 ATI Radeon Xpress 200M**

I've been fighting this issue for the last week.

I haven't posted before, as I've been trying to follow the threads already started about the new ati drivers instillation. Each attempt has been following a clean install of Ubuntu 5.10. Last night (Sunday, 6 February 2006) I finally gave up and used my Toshiba Recover Disk to reinstall Windows XP. :evil: After a &#8220;cooling off&#8221; period, I am ready to try again.

At this point, I have partitioned my HD to allow me to dual boot XP and Ubuntu.  The partition for Linux is approx. 37GB.  I **HAVE NOT** installed Ubuntu as of yet, but from past installs, this is what will happen: Upon install, X crashes. I have to edit the xorg.config file and add the following to the &#8220;Device&#8221; section to get X to work:
	option		&#8220;noaccel&#8221;

I have attempted to install Breezy's included ATI driver, but was stuck in 1024X768 (my monitor is 1280X800).

I started to follow the howto on the latest ATI fglrx driver install, but I had a problem with my WiFi. I have an integrated Atheros wireless card and when I followed the instructions related to the Madwifi drivers I lost the card (meaning It no longer showed up in my network settings).

I'm looking for specific advice on what to do just after install to get this resolved. If I need to post any message files, let me know what ones to post. I will most likely do the install tomorrow after work. 

Thanks in advance,

Kent

---

### Post by mlomker on 2006-03-01
Install the madwifi drivers using [this how-to]("http://ubuntuforums.org/showthread.php?t=105437") before upgrading to the latest ATI driver.

---

### Post by k5knt on 2006-03-01
I'm probably being dense here, but it has been one of those days. :???: 
Just to avoid any confusion.  I do a clean install, followed by installing the updates. 
Then I remove the restricted-modules package and install madwifi. Correct??

If so, would you then point me to where I get the information on installing the latest ati drivers?

Kent

---

### Post by shadowfist on 2006-04-16
well I dont have any answers for you because I am a very green ubuntu user. but I am interested in the answers because I have an a105 and havent been able to get any distros to boot properly (except DSL but i then couldnt get the internal wireless card to work).

I have tried the curent flight cd of dapper drake and it freezes at the "starting hardware drivers" stage. I am thinknig that this is the same problem you are having and if i could get the graphics drivers to work than I would be quite happy. if anyone has some help for us I am sure that we would be eternaly greatful. :-)

---

