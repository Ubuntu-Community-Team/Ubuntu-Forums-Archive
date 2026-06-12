---
title: "Monitor Mode Not Supported"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by 11BrathovdeA on 2011-04-25
Hi there,

I was trying to set the mode my wireless network interface in iwconfig to Monitor but it keeps coming up with an error message:

sudo iwconfig wlan0 mode Monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

I learned that you can change the mode in the iwconfig man, i think that my driver ndiswrapper doesn't support this mode. Is there a way to change my driver or install a new one that can support Monitor mode? Or am i making a mistake setting my network to Monitor mode? 

Thanks in advance,

11BrathovdeA

---

