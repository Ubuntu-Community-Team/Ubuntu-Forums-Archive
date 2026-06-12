---
title: "Network restart with my Linksys wifi card causes my system to crash/lock"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by dunnerz on 2006-02-19
Hi,

I've searched the forums for this problem, but can't seem to find any solutions.

As the subject says - when I do a 
sudo /etc/init.d/networking restart

all is fine for a few seconds, then the system locks up.... can't move the mouse etc, can't do ctrl+alt+backspace/del or ctrl+alt+f1  - complete lock up - the only solution is rebooting

I'm using Ubuntu Breezy (upto date is it can be) - and a Linksys wifi card (a 54mps version)  - using the bcmwl5 driver.

I would post more system information, but not sure what would help or be revlvant - so if anyone needs any info - just ask.

The problem has only just started to happen - although I would say I havent had to restart my network card recently, so I could track it down to the last month or so.


Any help would be very much appriciated.

Thanks.

---

### Post by bscbrit on 2006-02-19
You may get some clues by looking in your log files (/var/log/....). Look in syslog, messages and dmesg to see if there is anything there that looks wrong - error messages are usually easy to spot.

If that doesn't work, try following the wirelessTroubleshooting guide ([https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)) to see if that helps.

---

### Post by matt_risi on 2006-10-13
This same thing happens to me as well, I have a Broadcom card.

---

