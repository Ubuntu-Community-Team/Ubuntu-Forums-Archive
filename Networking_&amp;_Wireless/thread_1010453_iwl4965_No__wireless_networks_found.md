---
title: "iwl4965 No  wireless networks found"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by danblack101 on 2008-12-13
Hi,
I am having a few issues setting up my intel 5100 wireless. I followed this site 
[http://www.connect-utb.com/index.php?option=com_content&view=article&id=46:get-intel-wireless-wifi-link-5100-working-on-ubuntu-804&catid=34:linux]("http://www.connect-utb.com/index.php?option=com_content&view=article&id=46:get-intel-wireless-wifi-link-5100-working-on-ubuntu-804&catid=34:linux")

There are no networks found with wicd or with iwlist. 
I believe the AP here is on channel 13, but the driver only checks up to channel 10 (sudo iwlist wlan0 channel)

I have tried adding option cfg80211 ieee80211_regdom=EU to modprobe. But I still don't seem to be picking up any AP's.

Any suggestions about how to proceed?

Thanks

---

### Post by boterbram on 2008-12-13
First of all, the driver is not perfect yet, I myself am still experiencing some glitches.

But to try and help you: you will probably get some errors when typing sudo make unload during the process right? if so, first do 
```
sudo rmmod iwlagn && sudo rmmod iwlcore
```
(or the other way around, im not sure). This will solve these errors. If the problem still exists I don't think I can help, because putting the ucode in this folder and following the instructions on [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) just worked for me

hope this was it, else good luck

---

