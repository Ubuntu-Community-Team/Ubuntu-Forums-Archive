---
title: "Dual Monitor question"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by eweibust on 2006-08-29
What does it take to get a second monitor working with a laptop?  I have a HP zd8000 and a ViewSonic VA1912wb.

Do I have to "hand edit" the xorg.conf?  Is there a wizard?  I'm a bit nervous just hacking away at the xorg.conf.  If I do edit the file by hand is there a repository that has settings I can copy and paste from?

Thanks...

---

### Post by Thomas_tc on 2006-08-30
Hi,

at first make a backup: cp -p /etc/X11/xorg.conf{,.backup}

I published a part of my xorg.conf in [http://www.ubuntuforums.org/showthread.php?t=246446](http://www.ubuntuforums.org/showthread.php?t=246446). If you correct the lines with the technical datas of your hardware, it should work for you too:

You have to dublicate the "Device", "Monitor", and "Screen"- section in your xorg.conf and correct the entries for your external monitor. You've to add new lines in the Serverlayout - that's it. Just take a look on my xorg.conf

have fun,
Thomas_tc

---

### Post by eweibust on 2006-08-30
Thanks Thomas,

I'm not in the office today so I won't be able to test this until tomorrow.  One question, where do I get the technical data for my hardware?

Erik

---

### Post by Ziox on 2006-08-30
> **eweibust said:**
> Thanks Thomas,

I'm not in the office today so I won't be able to test this until tomorrow.  One question, where do I get the technical data for my hardware?

Erik

follow the Dual Monitor guide in my signature, it has a step-by-step guide and some troubleshoot options...

---

### Post by eweibust on 2006-08-31
Ziox,

I followed your Xinerama instructions, which were great, but was unsuccessful.  The odd thing is that after I rebooted my 2nd monitor worked and my laptop screen was blank?  Any ideas where to go next?

Erik

---

### Post by Ziox on 2006-08-31
post your xorg.conf file please, I had the same problem and add couple lines might just work...:)

---

