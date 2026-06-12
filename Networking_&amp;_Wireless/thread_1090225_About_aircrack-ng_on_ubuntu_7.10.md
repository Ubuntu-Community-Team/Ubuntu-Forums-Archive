---
title: "About aircrack-ng on ubuntu 7.10"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by aurora_consurgens on 2009-03-08
Hello GUys, I have a problem on ubuntu 7.04. I used aircrack v. 0.6.2-7 and when I try to 
# sudo airmon-ng start wlan0 

It says 

usage: airmon-ng <start|stop> <interface> [channel]    
Interface       Chipset         Driver    wmaster         Unknown         Unknown (MONITOR MODE NOT SUPPORTED)  wlan0           Unknown         Unknown (MONITOR MODE NOT SUPPORTED)  

I can't enabled Monitor mode.
How should I do?

thank.

---

### Post by kevdog on 2009-03-08
The ability to change to monitor mode is dependent on your wireless hardware and wireless driver or kernel module.  The only drivers I know that are compatible with monitor mode are madwifi, b43 (and some variants), realtek, and ra.  If you have used aircrack in the past, likely its not a hardware related issue, but now a problem with your wireless driver.  This information you are going to need to provide.

---

