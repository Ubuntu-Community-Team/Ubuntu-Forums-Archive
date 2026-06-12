---
title: "Auto-connect at boot"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by hobbit1983 on 2011-06-23
I am running 11.04 and have a netgear USB wireless NIC.  When I am logged in I can connect to the wireless network through the USB adapter without any problems.

I wish to use the machine as a part time home server and so have installed samba, LAMP etc however when I start the machine the NIC is not activated until I have logged in.

In the past I have done this but only ever over a wired ethernet connection, never wireless?

Can some one please point me in the right direction?

---

### Post by hobbit1983 on 2011-06-23
I have done some searching and found that I may be able to 
Add network-manager-gnome to the startup list.

I will try that and see if that helps

---

### Post by prshah on 2011-06-23
> **hobbit1983 said:**
> when I start the machine the NIC is not activated until I have logged in.

Please see this thread [HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.]("http://ubuntuforums.org/showthread.php?t=202834") for information on how to have wireless secured connections activated automatically on boot.

Please post back here if you need more help.

---

### Post by hobbit1983 on 2011-06-23
Thank you for your response. I will have a look at that link later today and let you know how I progress. 

Thanks again

---

### Post by hobbit1983 on 2011-06-30
Thanks for the link and help.  Because network-manager was able to connect to my access point I found that clicking 'make this connection available to all users' gave the desired effect and the NIC is activated at boot time

---

