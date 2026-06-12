---
title: "Dell Inspiron 1525 Disconnected..."
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by chaos945 on 2010-05-22
The internal sata died on my laptop so I thought I'd try to use an external usb enclosure with a Ubuntu install. Unfortunately Windows 7 does not let you install on USB or IEEE devices. How lame is that?

I am having trouble getting any network connections to initialize on Ubuntu after successfully installing 9.10 and 10.04 onto my sata laptop hard drive attached via usb from the enclosure.

On 9.10 I can see SSID's being broadcasted but I can't connect to my home one; it just says disconnected after a period of trying to connect. Also wired connections don't work; although it shows "Auto Eth2" and attempts to connect ending with "Disconnected". I have read there are problems with this model of Laptop and the driver support. So I decided to try a USB NetMate Ethernet device which resulted in the same issue as the internal network card. It is reported that a proprietary Broadcom driver is in use for the wireless on 9.10 but not in 10.04.

On 10.04 I can't even see SSID's, but all devices attempt to connect to a network then just say disconnected after a period.

I had this same issue with a live CD installation.

My skill level in Ubuntu is beginner at best, but I have aptitude to complete the steps suggested [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") regarding a possible solution using Ndiswrapper. However I would like a prettier solution is someone has any ideas.

This is kinda ironic since this model was distributed with Ubuntu 7.x when it came out....

---

