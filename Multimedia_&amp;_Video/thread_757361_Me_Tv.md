---
title: "Me Tv"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by jmore9 on 2008-04-16
I don't know if anyone has tried ME TV which is available on the launchpad.net site.
I got tired of trying to figure out how to convert a initial-tuning-data.txt file into a channels.conf that kaffeine would be able to use so i was wandering around the launchpad site and saw this app called ME TV.  I installed it and when it started up for the first time it saw it did not have a channels.conf so it asked if i wanted it to create one.

Of course i said yes and when it was done i had a channels conf file and it displayed the on demand channel on comcast -- the free version that they stick in on the clear qam.  But that is a big improvement from where i was.

I am now working on getting the rest of the channels in .  check it out as far as a channels.conf goes this is just as if not as easy as windows app for the {innacle 800i pci card.

---

### Post by xc3RnbFO8P on 2008-04-18
What I did was, I got channels for Copenhagen
```
DR1:714000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:111:131:101
```
I got my information from Kaffeine

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=66310&d=1208517357[/IMG]

and change the freq. from 714000000 to 602000000 in /home/my folder/.me-tv/channels.conf.

---

### Post by jonlowe on 2008-04-18
I'm also haveing troubles with ME TV.  I'm running Ubuntu 8.04.  ME TV finds the Hauppuge HVR-1500, and offers to scan.  It does, and produces a channels.conf file.  But then it says that there is an invalid entry in my channels.conf file, and only gives me the option to cancel and the pogram quits.  Any ideas?

Jon

---

### Post by xc3RnbFO8P on 2008-04-18
Check if you got /home/your folder/.me-tv/channels.conf,
if not you can make it in gedit, save as channels.conf.
In terminal: **gedit**

---

