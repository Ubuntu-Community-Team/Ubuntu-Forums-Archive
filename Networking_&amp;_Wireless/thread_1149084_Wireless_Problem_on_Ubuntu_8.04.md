---
title: "Wireless Problem on Ubuntu 8.04"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by mrmagpie on 2009-05-04
I installed Ubuntu 8.04 on my Inspiron 8600 a while back, but I very rarely use wireless on this computer, so when I noticed I was having trouble connecting to my wireless network at home, I didn't worry.

As it turned out, we did eventually end up having to replace our old wireless, and so on a whim I decided to try connecting again more recently. Still, to no effect. 

The nm_applet itself functions well, and I'm sure I've been putting in the correct security information for our WPA network at home, but the wireless simply refuses to connect.

I'm not sure if I'm posting this correctly or what information might be helpful for you to have, but if anyone has any idea where I should go from here I would appreciate your replies. :)

The alternative seems to be resigning myself to never figuring out the mystery.

---

### Post by Svensk023 on 2009-05-04
I would poke around the various threads in the wirless forum. There is already a plethrea of help there.

But just for my clarification. type the following in your terminal, then paste the results here

```
iwconfig
```

---

### Post by mrmagpie on 2009-05-05
I understand that, naturally, the threads in this forum are bound to have gone over my problem before.

However, not knowing exactly what my problem is, I can't say with any certainty how alike or unlike the problems other people pose are to my problem.

For your peace of mind, this is returned:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Svensk023 on 2009-05-05
hmmm...
My suggestion is to poke around the forums for some proper help. 
Sorry I couldn't assist you further

---

### Post by mrmagpie on 2009-05-05
No problem.

Thank you anyway. :)

---

### Post by mrmagpie on 2009-05-05
Not that this seems to be anything new, having surfed the wild blue yonder of the Ubuntu forums for a while, but my radio frequency kill switch is on. Did we ever discover a way to turn it off?

---

### Post by kilgore9 on 2009-05-05
Hey there.  I solved lots of my problems with wireless using wicd, though I'm about to post another topic about further problems in that area.  You may also need a driver for your wireless card....If you search for threads created by me, kilgore9, (there aren't many) you will see my wireless threads with some useful info....

---

### Post by mrmagpie on 2009-05-05
Thank you very much for your reply. I will definitely do that.

I was wondering, though, why would I suddenly need to replace my driver? Wireless worked just fine for me before I made the switch from XP to Ubuntu - does something happen during the installation process?

---

