---
title: "How do I stop automatic ppp dialup on boot?"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by boon on 2006-06-19
I've managed to configure and connect to the internet with my winmodem using the pppconfig utility and commands pon/poff.

But when I boot the machine it seems to automatically try and dialup (but is unsuccessful). This locks the phone line and I am reduced to manually disconnecting the phone to get back to a dial tone. Then I can use pon to dialup successfully when I want.

How do I disable this process from occurring at boot? I only want to dialup when I command it to (or maybe when I start a net program like firefox.)

---

### Post by www.rzr.online.fr on 2006-07-16
> **boon said:**
> 
How do I disable this process from occurring at boot? I only want to dialup when I command it to (or maybe when I start a net program like firefox.)

there a file to avoid that ... something like /etc/ppp/*boot*
isnt it ?

---

### Post by boon on 2006-08-14
well, I'm happy to report that since i upgraded to 6.06 the problem seems to have resolved itself. ppp does not start automatically at boot, and operates normally using pon/poff commands.

I can also report on my upgrade experience. I tried to upgrade with dialup. This took hours (naturally) to download, until the modem connection was lost (as does happen of course). The upgrade process was aborted and furthermore I was unable to resume the download at the point where it stopped. Conclusion: upgrade via dialup is effectively impossible.

Next i obtained from shipit the 6.06 disk. This simply does not allow upgrade of 5.04 to 6.06. Instead an alternate disk is needed, which is not supplied but which you can download. (!)

Finally i was lucky enough to gain temporary access to a broadband connection. Updgrading via the Update Manager worked beautifully, without a single hitch. 

Clearly things are geared to broadband use. But there are still lots of people on dialup, are there not, especially in 'third world' countries?

---

