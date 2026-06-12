---
title: "DWA-130 needs password always"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by AndersA on 2009-09-07
Hi guys,
I am brand-new to both Ubuntu & Linux.
Install went well (9.04), & I have D-Link DWA-130 configured using ndiswrapper.
I am using WPA & TKIP on my router.
My system asks for the password repeatedly but will not ever connect.
I have been searching for answers for the past week, but they are hugely confusing & often assume I know more than I do.
I'm hoping someone has time to walk me through this??

Thank.

---

### Post by bkratz on 2009-09-07
> **AndersA said:**
> Hi guys,
I am brand-new to both Ubuntu & Linux.
Install went well (9.04), & I have D-Link DWA-130 configured using ndiswrapper.
I am using WPA & TKIP on my router.
My system asks for the password repeatedly but will not ever connect.
I have been searching for answers for the past week, but they are hugely confusing & often assume I know more than I do.
I'm hoping someone has time to walk me through this??

Thank.

I have been using my DWA-130 under ndiswrapper since version 8.10. Initially, I was not able to connect with either wep or standard wpa. The conditions I have setup are WPA2 with AES. I admit I haven't tried the other options since I finally got it to work, so maybe something else caused these original issues.  I would be happy to help you, just pm me.  By the way do you know if you have version A, B or C?

---

### Post by AndersA on 2009-09-07
> **bkratz said:**
> I have been using my DWA-130 under ndiswrapper since version 8.10. Initially, I was not able to connect with either wep or standard wpa. The conditions I have setup are WPA2 with AES. I admit I haven't tried the other options since I finally got it to work, so maybe something else caused these original issues.  I would be happy to help you, just pm me.  By the way do you know if you have version A, B or C?

  Thanks, I will try it tonight. My DWA-130 is version A. According to the posts I have seen so far, ndiswrapper is the only way it is supported.

---

### Post by bkratz on 2009-09-07
> **AndersA said:**
> Thanks, I will try it tonight. My DWA-130 is version A. According to the posts I have seen so far, ndiswrapper is the only way it is supported.



Mine is an A also.  Try either unsecurred (just for testing) or WPA2 with AES, WPA is no longer secure, it only takes about a minute or two to break; so you should change anyway.

If it works make sure to mark the thread "solved"

Good Luck!

---

### Post by AndersA on 2009-09-08
> **bkratz said:**
> Mine is an A also.  Try either unsecurred (just for testing) or WPA2 with AES, WPA is no longer secure, it only takes about a minute or two to break; so you should change anyway.

If it works make sure to mark the thread &quot;solved&quot;

Good Luck!

OK, I am flummoxed!! I have tried: WPA with both AES & TKIP WPA2 with both AES & TKIP WPA@\2-Auto with both AES & TKIP  My testing procedure was as follows: Set router to no security Test connection Disable Wifi Delete Wifi connection Set router to secure setting for with AES enable Wifi Test connection Disable Wifi Delete Wifi connection Set router to secure setting for with TKIP enable Wifi Test connection repeat, starting again with no security.  Unsecure: always connected. All secure settings failed with the exception of WPA2-Auto, which worked the very first time only. I tried it 5 times more and it always failed.  Any thoughts on where to go from here?

---

### Post by bkratz on 2009-09-08
> **AndersA said:**
> OK, I am flummoxed!! I have tried: WPA with both AES & TKIP WPA2 with both AES & TKIP WPA@\2-Auto with both AES & TKIP  My testing procedure was as follows: Set router to no security Test connection Disable Wifi Delete Wifi connection Set router to secure setting for with AES enable Wifi Test connection Disable Wifi Delete Wifi connection Set router to secure setting for with TKIP enable Wifi Test connection repeat, starting again with no security.  Unsecure: always connected. All secure settings failed with the exception of WPA2-Auto, which worked the very first time only. I tried it 5 times more and it always failed.  Any thoughts on where to go from here?


 sorry, I really didn't understand the procedure you described above.  If I can figure out how to embed screen saved images into a private message, I will send all the setup screens under the network icon in my system.

---

### Post by AndersA on 2009-09-12
Thanks for the help.

The short results are that I can always connect with no security on my router, and that when I set it for ANY variation of WPA it will never connect. as per your suggestion, here is the output of 'lshw -C Network:

  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:3b:5a:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=xxx.xxx.xxx.xxx latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:58:3e:ff:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Marvell,11/27/2006,1.0.4.9 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:9b:5c:18:de:f3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I 'Xed' out my IP address in the listing.
Anyone have any thoughts?

---

### Post by Blackthorne2 on 2010-01-11
No idea why this is posted as solved. There is no solution posted here....

---

### Post by bkratz on 2010-01-11
> **Blackthorne2 said:**
> No idea why this is posted as solved. There is no solution posted here....

I believe we did it through email and he actually solved the problem. Why do you have one also?

---

### Post by fredthomke on 2010-04-12
At the risk of "hijacking" someone else's thread, I DO have a similar problem: I can connect to my router if I turn off the router's security. If the router has ANY security (WEP, WPA, WPA-PSK) I cannot connect, even with a simple key such as "1234567890". I have other XP laptops that can connect with no problem to the router, even when the router has a secure password. But on my Ubuntu laptop, with Network-Manager, it's a no go for security.
 
If someone is successful with a solution, PLEASE post the solution, even if you did it via PM-ing!!! That will help the rest of us with similar problems! Otherwise, you leave us hanging!
 
Thanks!

---

