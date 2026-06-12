---
title: "Need driver for Asus PCE- N53 wireless I/O card"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by HilltopSC on 2013-06-28
Asus, for its most recent Linux release of drivers, is for kernel dated to 2008. Is there a way to get 13.04 to recognize the card, let alone, get it up to 300mps download speed? While greatly appreciative of Ubuntu and Linux in general, I am NOT a programer, therefore, one may have to 'dumb-down' some advice.

In order to use Asus's Linux drivers for kernel v2.6, must I revert to 8.04? 101010?

Has someone already written a driver for this card to operate in later versions of Ubuntu?

Per Asus, the PCE-N53 uses a Qualcomm chip. Problems related to chip or just lazy programming priority by Asus?

---

### Post by Dawscaus on 2013-07-02
I got mine working using the original driver and a patch I found on an archlinux forum I will post a link tomorrow. I feel like this card should be better supported than this. I have never had problems with wireless cards before this one.

---

### Post by DavidKleman on 2013-07-09
Please post the driver you posted. Would be very helpful. Tried to locate but no dice. Thanks!

---

### Post by Dawscaus on 2013-07-16
Below is the link to what I used. What you want to do is download the Asus linux driver off their website then use the patch found in post 17 in the link below. Message back here if you get it working or if you did not. I will do my best to answer your questions as well of you run into problems. I apologize for not posting earlier. 

[https://bbs.archlinux.org/viewtopic.php?id=152960](https://bbs.archlinux.org/viewtopic.php?id=152960)

---

### Post by Dawscaus on 2013-07-30
quick update. Each time I let the ubuntu updates run I have had to repeat the patched driver install. This involved me navigating to the patched drivers directory then run "make install"and then run "modprobe 5592sta" to initialize the card.

---

