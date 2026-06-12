---
title: "No wireless on 8.10 fresh install (LG E500 laptop)"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Valshar on 2009-01-01
So, clicking on Network Manager shows no wireless connection. It's not that I can't find my connection, the problem is there isn't even a connection under Wireless (as there is Auto eth0 for the Wired connection I'm using).

lspci returns this (wireless):

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)



and iwconfig returns:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



I don't really know what to do, I'd really appreciate some help!

---

### Post by Kobalt on 2009-01-01
Hello, 

You need to install the restricted driver to get your card working. To do so, open up a Terminal and enter the following command line : ```
sudo aptitude install linux-backports-modules-intrepid
```

Then you'll be able to enable this driver from System > Admin. > Restricted drivers manager

---

### Post by Valshar on 2009-01-01
Hum, I just did that, installed it, went to Hardware Drivers but it shows that there is already a driver in use: "Support for Atheros 802.11 wireless LAN cards." There is no other option for wireless.

---

### Post by Valshar on 2009-01-03
help? :???:

---

### Post by Valshar on 2009-01-09
still haven't fixed this...

---

### Post by slavos on 2009-01-09
I wish someone could help out here. I am a new Linux user as of today. I was hoping the install would auto detect my wireless internet. The troubleshooting is great at telling me what to check, but not so great at telling me what to do if I'm not getting what I'm supposed to! It's a little frustrating. 

I'm looking at my Hardware Drivers, and I do see that I have an "Antheros Hardware Access Layer (HAL)" and "Support for Atheros 802.11 wireless LAN cards", both enabled and in use. 

My iwconfig also gives me "lo no wireless extensions" and "eth0 no wireless extensions".


I have no idea where to go from here....

---

### Post by us3rX on 2009-01-10
I am in the same boat, any insight would be greatful XD

~us3rX

---

### Post by slavos on 2009-01-11
Okay, I got this worked out on another ubuntu forum. It turns out it was my chipset, and I had to do all kinds of crazy things to get connected with wireless (I could connect direct with LAN cable). Check out my saga at:

[https://answers.launchpad.net/ubuntu/+question/56993](https://answers.launchpad.net/ubuntu/+question/56993)

"AR242x wireless chipset not working in Ubuntu"

There is a yellow star in the box of the procedure that finally got me going. I didn't have to follow the final steps that Mark suggested.

---

