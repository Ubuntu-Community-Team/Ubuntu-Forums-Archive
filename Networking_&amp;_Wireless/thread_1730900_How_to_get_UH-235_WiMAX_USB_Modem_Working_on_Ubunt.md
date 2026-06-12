---
title: "How to get UH-235 WiMAX USB Modem Working on Ubuntu"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by aisajib on 2011-04-16
Hi everyone! Imagine this scenario at my home: I'm working on my laptop using WLAN receiver as I have a router installed at my home. Suddenly the electricity fails (it's a regular incident here in Bangladesh called Load-shedding) and the power source to modem and router dies. As a result, my internet connection drops. To connect to the internet without power, I use this QUBEE UH-235 WiMAX USB Modem. Now I know QUBEE may not be there in your country. But after a bit of research I figured that this UH-235 modem is common in almost every country. QUBEE just branded its logo on the device and the software within.

[IMG]http://www.blogkori.com/wp-content/uploads/2011/02/Qubee-UH-235-wimax-modem.jpg[/IMG]
This one is not my device, [mine is here]("http://www.flickr.com/photos/aisajib/5554783848/in/photostream").


In my windows, the software is installed as soon as I plug in the USB. That software then detects the modem, scans for network, and then connects to the internet. No extra CD is required for this. However, on an Ubuntu machine, I can't get it working. I guess there are ways to get this UH-235 modem working on my Ubuntu machine. This is keeping me from using Ubuntu as you know I'll have to restart and log in to WIndows whenever electricity is off as Ubuntu works with Wi-Fi, not this UH-235 modem when the Wi-Fi is out of power.

For the record, I'm using Ubuntu 10.10.

Any help from anyone?

---

### Post by josephmills on 2011-04-16
log into your modem and look for odd things. are you static are you dhcp so you port forward at all?

---

### Post by aisajib on 2011-04-17
> **josephmills said:**
> log into your modem and look for odd things. are you static are you dhcp so you port forward at all?


All the information I get from the modem software is quoted here for your reference.

There are IP Address, Subnet Mask, DNS Server, MAC address and under the WiMAX Info tab there are RSSI, CINR, Tx Power and NAP ID. Of course there is an Authentication Tab where I need to enter my WiMAX user ID and password to get connected with the station.

Anyhow I can get it working on Ubuntu?

---

### Post by skjamil on 2011-06-13
Hi Sajib, 

I am also experiencing the same problem. How did you solve this issue? Thanks for letting me know. 

Regards
Jamil

---

### Post by aisajib on 2011-06-14
> **skjamil said:**
> Hi Sajib, 

I am also experiencing the same problem. How did you solve this issue? Thanks for letting me know. 

Regards
Jamil

The issue is still unresolved as you can see.

---

### Post by ampc on 2011-07-14
Here is how i am dealing with this problem.

1. You can install Win XP in wmware player.
2. Your qubee device will work in Win XP.
3. Share internet from Win XP to Ubuntu using ICS.

However, this method is resource hungry (:()

Cheers,
Mannan PK.

---

### Post by Captvolcan on 2012-01-20
Im also from Bangladesh! The software we see in Win7 or XP is not provided by the producer of UH 235 but from qubee! They have the necessery driver to install the device and provide with additional software to log into their network! I don't know if they created something like that for Linux but if they didn't i'd be next to impossible to install it. Because firstly we need to find the driver for the device for Linux. Then we need a software that can do the DNS, SuB, MAC etc and can use account name n password to log in! I don't think anyone other than Qubee can do that. So better ask qubee for it! I mailed them and waiting for reply

---

