---
title: "Network Manager Ubuntu 9.10"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by Daftk on 2009-11-04
Hello Everyone,
 
I have a Lenovo Thinkpad T400 laptop. I finally got bored of windows and decided to go to a different OS. I wiped my hard drive and installed Ubuntu 9.10 .
 
The installation went well from my limited knowlegde. I am no experiencing an issue with the Network Manager. When i connect a Ethernet cable it will give me a message saying "Wired Network Disconnected".
 
I then proceeded to ensure that i have the drivers installed for  the network card which i do. I did a ifconfig and see its not getting an IP.
 
I googled this issue and alot of people are having issues with this. I am completely new to Ubuntu so any help shall be appreciated in resolving this issue.
 
Also the wireless does the same thing, it detects wireless networks in range, when i connect to any, it will then proceed to state "Wireless Network has been Disconnected" and i get not IP if i do ifconfig on it.
 
Thanks in advancve to all the folks that shall be trying to assit me here.
 
Regards,
 
Kamran

---

### Post by oktapod on 2009-11-13
I had the same issue today.
But all hapened because it was a ADSL connection. I'm gone give a try tomorrow with the **$ sudo pppoeconf** command from terminal.
Maybe you have a ADSL connection too.It seems like ADSL connection isn't auto configured like normal LAN connection.
Hope helps.
Let me know.

---

### Post by SawyerLX on 2009-11-18
I am just waiting for the updates, then testing nm-applet.
But, I messed with the start-up and it won't come back.  I have MINT8 too, but I'll have to reinstall 9.10 for the earliest fix; i guess. also using pppoeconf.

---

