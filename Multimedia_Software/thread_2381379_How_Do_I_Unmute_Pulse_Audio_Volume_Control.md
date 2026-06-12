---
title: "How Do I Unmute Pulse Audio Volume Control?"
date: 2017-12-30
forum: Multimedia Software
---

### Post by wbee on 2017-12-30
It shows both the input and output functions muted,but I can't remove the,"x", s?

How do I do the un mutes,to remove the x s?

Thank you.

(Moderator,yes,I have another post below but thought I would try this rather than bump that one.)

---

### Post by Autodave on 2017-12-30
What are the specs of your machine?  They may help some one help you.

---

### Post by wbee on 2017-12-30
Autodave,

I''m not sure I understand which specs I should include?

---

### Post by wbee on 2017-12-30
Based on some Google searching ,I opened the terminal and entered this:


```
sudo lshw |grep -A9 Audio 
```

It flashed PCI for perhaps a second and disappeared. Then it flashed USB  and disappeared. This it flashed SCSU and disappeared?

Is that a clue helpful to anybody?

---

### Post by Yellow Pasque on 2017-12-31
> **wbee said:**
> Is that a clue helpful to anybody?

No.

Start here: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by wbee on 2018-01-02
Thank you, Temüjin. That was useful.

---

### Post by Yellow Pasque on 2018-01-02
> **wbee said:**
> Thank you, Temüjin. That was useful.

I'm glad you feel that way, but it's not useful to the folks trying to help you if you don't share the link to your info.

---

### Post by wbee on 2018-01-03
I have my software updater set to report to me once a week and then I download those when I don't have lots of stuff running.  When I downloaded the latest updates,after performing the requested restart,the sound was working.

So while I don't know what was specifically wrong,I do know that update included a pulse audio update from watching stuff load. 

But I did learn something,having read the two sticky tutorials at the top of this category and  theses two pages:

[https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting)
[https://wiki.archlinux.org/index.php/PulseAudio](https://wiki.archlinux.org/index.php/PulseAudio)

Also,thanks to Temujin for the reporting and what to report if something weird happens again.

SOLVED

-----------

Thank you.

---

