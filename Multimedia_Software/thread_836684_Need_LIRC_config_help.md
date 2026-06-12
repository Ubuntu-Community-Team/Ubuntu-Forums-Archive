---
title: "Need LIRC config help"
date: 2008-06-21
forum: Multimedia Software
---

### Post by Livin on 2008-06-21
I have spent 2 days searching this forum, googling, and reading all the how-to's and troubleshooting threads I could find, not a single thing has worked.

My setup...

Ubuntu x64 8.04 ... all updates installed
LIRC 0.8.3 pre1 ... installed using package manager
USB-UIRT ... computer detects device fine, works on XP fine
XBOX remote

I have tried so many different hardware.conf I lost count. Half the time IRW throws a 'Connection refused' and the rest it just sits there waiting so it must not be detecting any IR.

I'm confused as to what MODULES and DRIVERS I should be loading in the conf?

Anyone got a USB-UIRT working on 8.04?

Thank you for any help you can give to this Linux noobie.

---

### Post by Livin on 2008-06-22
a little help please. :KS

---

### Post by Livin on 2008-06-24
2 days an no help... :confused:

I'm a linux noobie trying to learn and get some help on something without a ton of info/docs out there and you guys sure make it difficult.

This UIRT works fine in Windoz and takes 30 seconds to get it running. Linux is not that simple but I'm trying.

I like Linux and want to keep using it... please help.

---

### Post by Livin on 2008-06-26
Amazing... no help at all, not even on the SF LIRC forum.

Very sad. I expected more from this community.

---

### Post by Scorpuk on 2008-06-26
Have you tried using irrecord to create a config file for your remote?


```
irrecord new-lircd.conf
```


If this works for you it will create a lircd.conf file for your remote.


[http://www.lirc.org/html/irrecord.html]("http://www.lirc.org/html/irrecord.html")

---

### Post by Livin on 2008-06-26
I don't believe I would need to make my own... The codes are just standard XBOX codes that I've been using for 4 years. If IRW sit there doing nothing I suspect that it is a problem with the LIRC setup, not the codes?

---

