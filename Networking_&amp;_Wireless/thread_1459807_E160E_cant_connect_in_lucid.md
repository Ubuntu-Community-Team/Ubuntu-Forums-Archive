---
title: "E160E cant connect in lucid"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by soulseek on 2010-04-21
I'm trying to connect with E160E to kanguru (portuguese provider). I'm using the default configuration to my provider.

On UNR 9.04 the same configuration worked well.

On Lucid I keep getting:

```

Apr 22 04:07:43 sudoeste-laptop pppd[4011]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 22 04:07:43 sudoeste-laptop pppd[4011]: CHAP authentication succeeded
Apr 22 04:07:43 sudoeste-laptop pppd[4011]: CHAP authentication succeeded
Apr 22 04:07:49 sudoeste-laptop pppd[4011]: Modem hangup
Apr 22 04:07:49 sudoeste-laptop pppd[4011]: Connection terminated

``` 

Any ideas ? Thx

---

### Post by pdc on 2010-04-22
lucid lynx is being developed;

here is the forum for it

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

the advice there says: 

**Ubuntu Lucid Lynx is in development, use only for testing purposes!!!**

so if you are testing it, report on that forum

further it says:

 Please note: Ubuntu Developers do not usually read the forums, to report a problem found in Lucid please report the bug in Launchpad.

---

### Post by soulseek on 2010-04-22
tried on 9.10 and the problem is the same

---

### Post by soulseek on 2010-04-22
The problem was with the APN settings as the provider changed them.

All OK now

---

### Post by lutra on 2010-07-01
> **soulseek said:**
> The problem was with the APN settings as the provider changed them.

All OK now

Hi soulseek,
what are the correct parameters for the connection to the Kanguru provider? I have no problem with TMN but I'm struggling with Kanguru.

Thanks in advance

---

### Post by morganzine on 2010-09-24
Kanguru has changed is APN, that is no longer "myconnection" but "kanguru-portatil" for instance, because each package available has is own.
 
Please check where: [http://androidpt.com/index.php?option=com_kunena&Itemid=3&func=view&catid=71&id=46619&limit=10&limitstart=10#47818](http://androidpt.com/index.php?option=com_kunena&Itemid=3&func=view&catid=71&id=46619&limit=10&limitstart=10#47818)

---

