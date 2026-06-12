---
title: "Can my Broadcom Corporation BCM4312 wireless card allow package injection??"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by -=Ghost=- on 2009-05-26
I have a laptop with a Broadcom BCM4312 wireless card.
and I would like to know if it is possible to allow package injection form it??

Also, If it is possible, What is the correct driver I should use to allow the above??

Can anyone point me in the right direction. Or even guide me through the process of patching my above wireless card with the correct patched driver fo my card to allow package injection?? 

Thank's in advance...

---

### Post by Ayuthia on 2009-05-26
You will need to check in the Terminal to see if you have the 14e4:4315 chipset:
```
lspci -nn
```
If you do, then it will not work.  Otherwise you should be able to do it with the b43 module.

---

### Post by -=Ghost=- on 2009-05-26
Hi, Thank's for replying..

Here is the output from:  lspci -nn

04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

---

### Post by -=Ghost=- on 2009-05-26
I am trying to install and use the b43 module.

But I must admit I am having some trouble finding and instaling the the right b43 module!!

Can anybody advise me on how to do this??

---

### Post by Ayuthia on 2009-05-27
You have a 14e4:4315 chipset so your card is not supported by the b43 module at this time.  Currently there are no options for you that will allow you to do packet injections.

---

### Post by -=Ghost=- on 2009-05-27
Okay thank-you for pointing that out.
although i am pretty dissapointed.

I have a Buffalo Buffalo wli-u2-kg54-ai WLAN USB adapter.
How can I find if this would allow package injection?
Do you know anything about this adapter??

---

### Post by Ayuthia on 2009-05-27
From what I can find, it looks like it uses the rt2500 module:
[http://ralink.rapla.net/](http://ralink.rapla.net/)

If that is the case, you should be able to use it for packet injection.

---

