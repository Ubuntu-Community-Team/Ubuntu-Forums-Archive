---
title: "BCM4315 Dell Mini 9 wireless monitoring"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by sir_nasty on 2009-04-15
so after reading/searching (yes I can use search!) through plenty of info I wanted to make a quick post.  I have a Dell mini 9 910, dmesg shows broadcom BCM4312 (rev 01), lspci shows BCM4315 5.10.27.9.

As I've read monitoring mode drivers are not available for this as of yet :( unless that's changed?

What I need, a utility of some sort that will show me the networks in range and what channel they are on, and that's it!  I'm semi noob to linux but as of yet aside from kismet, aircrack-ng (those two aren't compatible yet) I can't find a utility or easy way to determine this information.  Any help on a utility to use would be much appreciated.

---

### Post by Ayuthia on 2009-04-15
Monitor mode is not available yet for your card.  The b43 team has completed the reverse-engineering and currently working on the specs.

---

### Post by sir_nasty on 2009-04-15
I knew they were working on it and perhaps I'm to jacked up on coffee to fully understand but....

Does it require monitor mode to find what wireless channel various networks are on?  because right now I can see plenty of networks just can't get any info about what channel they are using.  Sorry for being a noob just need some clarity. thanks

---

### Post by Ayuthia on 2009-04-15
> **sir_nasty said:**
> I knew they were working on it and perhaps I'm to jacked up on coffee to fully understand but....

Does it require monitor mode to find what wireless channel various networks are on?  because right now I can see plenty of networks just can't get any info about what channel they are using.  Sorry for being a noob just need some clarity. thanks

It does not require monitor mode to find out this information.  Based on the information that this topic seems to be about, it does not look like you are trying to do things on your own network. Because of this, we really are not allowed to provide this information because it breaks the forum rules.

---

### Post by sir_nasty on 2009-04-16
I am a technician for an ISP and unfamiliar with linux.  All I want to be able to figure out is what channel the other wireless networks in the area are running on so I can decipher what channel to setup the new install on.  All this information is readily available in windows, I don't want to snoop or sniff just want to know what channel is the least used.  And how to do it with Ubuntu

---

### Post by superprash2003 on 2009-04-16
type **iwlist scanning** in your terminal.you should see the channel used by the wifi router in that..

---

### Post by sir_nasty on 2009-04-16
interface doesn't support scanning is the response I get.  Unfortunately I can't even run wine with xp because the drive isn't big enough, yet.... 

Any other ideas?

---

### Post by superprash2003 on 2009-04-17
type **sudo iwlist scanning**

---

### Post by StuartN on 2009-04-17
> **superprash2003 said:**
> type **sudo iwlist scanning**

Thanks so much Superprash, I would never have guessed that an interface that "doesn't support scanning" for ordinary users would be able to do so for a superuser!

The output is very useful because I live between two sets of apartments and it shows if any new router has used the same channel as mine.

---

### Post by sir_nasty on 2009-04-17
PERFECT!  That's exactly what I needed.  Also, stuarts situation is exactly what I run into on a regular basis when installing new service so this will prove a very useful tool in my arsenal!

---

