---
title: "Netgear(Broadcom) Wireless Adapter not working"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by Raoc3 on 2012-07-15
So I have not been able to find anyone with this exact issue.
 
I have recently installed Ubuntu 12.04. I am using a Netgear N300 Wireless adapter (WNA3100, BCM43231)
 
I have installed ndiswrapper, and used it to successfully install the driver for this adapter (bcmwlhigh5.inf)
 
The adapter shows as being installed, and I am able to detect the various wifi networks around me, including my own. Am am not, however able to connect to my wireless router. I am able to connect to my phone while in hotspot mode, and my windows computer can connect to my router, so it appears that everything involved is functioning properly, but I am not able to connect my Ubuntu desktop to my router. Both the adapter and router are Netgear N300 items. I don't understand what the issue here could be.
 
Any suggestions are appreciated.
 
Thanks!

---

### Post by ajgreeny on 2012-07-15
Can you connect to any non password-protected wireless, assuming there are some that you can try.  If there are no non-protected wireless connections you can try out, temporarily remove the WPA or WEP from yours and try that.  I have a netgear WG511v2 pcmcia card that for some time would not connect to any protected wireless, then over time WEP became possible, and eventually with newer kernels, WPA also was OK.  This was also using the windows driver with ndiswrapper.

It may not be wise, or even possible, for you to always run an unprotected wireless system, but it may at least give you a clue as to what is going on.

---

### Post by ranger1021994 on 2012-07-15
U have secure or insecure connection ?

---

### Post by Raoc3 on 2012-07-15
I've been looking at that possibility.  Both connections, my router and my hotspot are using WPA2 security.  I found that I am able to connect to my router when it is set to no security or WPA, but it appears to time out under WPA2.

---

### Post by himanshutanwar on 2012-12-01
i am facing the exact same problem.Did you find a way out??

---

