---
title: "Broadcom wireless on Ubuntu 12.04"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by goonybird on 2012-08-25
Hi folks.

There seems to be a common problem with Broadcom and Ubuntu but I cannot find my particular issue among the threads.

I have just (yesterday) installed Pangolin on my Acer 9300 and it didn't pick up the built-in wireless so I used a usb adapter. I have since installed drivers for Broadcom and nVidia through "Additional Drivers" as the system suggested and they are installed and activated ok, (so it says). 

But I still can't use the built-in wireless, only the dongle. I have re-booted without the dongle but it will not pick up the built-in wireless. 

Any clues please.

---

### Post by Hey Gary on 2012-08-25
I have a Dell D800, loaded Xubuntu 12.4, and all looked good except no wireless. I struggled several weeks. Today I happened upon this page in the forum. I downloaded the zip, followed the instructions and I am looking at the laptop with wifi working!

 The wifi chipset on my D800 is BCM4309.

 The forum page with my solution is:
[http://ubuntuforums.org/showthread.php?p=11413327](http://ubuntuforums.org/showthread.php?p=11413327)

 You want to look at post #11 from Wild Man.

 I hope this solves your problems, it was driving me batty too!!!

---

### Post by goonybird on 2012-08-26
Hey Gary, thanks for that...

Didn't work for me!?

Just checked 'Additional Drivers' again. It has the Broadcom STA driver as "activated but not currently in use". What can I do about that?

---

### Post by goonybird on 2012-08-26
Just for the record... to quote young Anakin... it's working!!

I followed what Hey Gary suggested for a second time and nothing happened.

I decided to try re-installing the Broadcom STA drivers. I removed them and shutdown. When I re-booted everything was fine!!

_A point to note_ - if the Broadcom STA additional drivers don't work it may be a good idea to remove them. There may be a conflict when trying other solutions. I have tried many different methods I found on this forum after I tried installing the Broadcom ones and nothing worked. The above solution didn't work till after the Broadcom drivers were removed. Worth bearing in mind. 

Many thanks again to all who help and to Hey Gary for this solution.

---

