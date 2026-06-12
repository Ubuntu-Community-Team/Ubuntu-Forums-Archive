---
title: "trying to get HDTV card working"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by nwr222 on 2007-02-26
I am attempting to get MythTv going. I am trying early steps following in [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php).  The scan fails,  but I think that I have a basic problem.  There is no /dev/dvb directory.  I gather from [http://www.linuxtv.org/wiki/index.php/First_steps_with_a_DVB_card](http://www.linuxtv.org/wiki/index.php/First_steps_with_a_DVB_card) this is a problem.

My card is FusionHDTV Pro.
It is recognised in the device manager.
I see the following entries from the startup

$ grep dvb /var/log/messages..
Feb 26 21:41:07 nrees-desktop kernel: [17179585.484000] cx2388x dvb driver version 0.0.5 loaded
$ grep DVB /var/log/messages
Feb 26 21:41:07 nrees-desktop kernel: [17179585.448000] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus

I don't see any of the errors indicating that this is an older card which requres firmware to be installed.  I can't see any attempt to register the frontend

---

### Post by BennBuntu on 2007-06-10
Have you had any luck? 
I tried but failed a few months back.
Dvico fusionHDTV PRO card with knoppmyth and ubuntu. I Read somewhere that it wasn't supported in the kernel and gave up. I'll be trying again with the new version of knoppmyth (R5F1) in the next few weeks. 

benn

---

