---
title: "Huawei e1752 mobile dongle keeps disconnecting"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by richardandrews on 2011-08-18
Hello all

I have been having a problem with my Huawei dongle now for about a week now, it keeps disconnecting every few minutes, I am not sure why it has started doing this (Kernel update possibly)? It has been running fine for a number of months.
I'm running ubuntu 10.4 Lts kernel version: 2.6.32-33 on a 32bit system, some of the relevant messages log has been attached, any thoughts are welcome, thank you

---

### Post by alexfish on 2011-08-19
Hi some ISP have been Hickey over last few weeks , some also been affected by the weather (poor signal quality) , if ISP alows it ,can try Network Manager with open nics or google DNS servers see if things improve

Added : note pppd trying to connect method = chap ; try using PAP

alexfish

---

### Post by richardandrews on 2011-08-19
Thank you for your time, alexfish, but I'm not sure if I fully understand what you mean, I have tried changing the settings in network manager now, I unchecked everything but PAP (under the ppp settings tab using the configure methods button - if that's what you mean), unfortunately that hasn't made a difference. 

Is there a possibility of getting a high bill or anything bad from using the different servers? I am using orange plan with APN: consumerbroadband but I can't speak to orange as I don't pay the bill.

Regards Richard

---

### Post by alexfish on 2011-08-23
Hi most of the info can be found in post #1 [How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

also consider using sakis3g ,there is a how to install, same thread. if download check out the wiki pages as to its usage (command line) 

see how it goes

regards

alexfish

---

### Post by richardandrews on 2011-09-19
Thanks for the info and links alexfish, it turns out the dongle is the problem, its doing the same in windows.
 
Thank you

Richard

---

