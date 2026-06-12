---
title: "Wireless connection however no Internet solved only temporarily"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by Stefan_Vogel on 2013-08-16
I am a newbie and just today installed Ubuntu 12.04 on my ThinkPad W500 w/o problems only that wireless connection is connected however does not allow me internet access. Cable connection works fine, also wireless from other devices including this notebook today when I stilled used Windows 7.

I read many similar posts and tried many suggestions one of which works partly. If I run the following...
   sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1

[FONT=arial]...I get perfect wireless connection with Internet access, until the next reboot. How can I make this change permanent?

Can anybody help?
[/FONT]

---

### Post by chili555 on 2013-08-16
Back to the terminal:```
sudo -i
echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf
exit
```You should be all set.

---

### Post by Stefan_Vogel on 2013-08-17
Hi chili555, that works fine. Thanks a lot!

So I created this config file iwlwifi.conf with the option that seems to help. Now, just to help me understand what this is: Any idea what the option...
options iwlwifi 11n_disable=1
[FONT=arial]
... actually does and why it helps? Thanks in advance to shed some light on the secrets of wireless options...[/FONT]

---

### Post by chili555 on 2013-08-18
> **Stefan_Vogel said:**
> Hi chili555, that works fine. Thanks a lot!

So I created this config file iwlwifi.conf with the option that seems to help. Now, just to help me understand what this is: Any idea what the option...
options iwlwifi 11n_disable=1
[FONT=arial]
... actually does and why it helps? Thanks in advance to shed some light on the secrets of wireless options...[/FONT]It disables N speeds. It corrects a well-known and long-lasting bug with 802.11N implementation in the iwlwifi driver. It is actually probably an issue between the driver, hardware and the router because some instances, including my own, work perfectly with N speeds. I'm confident that Intel and the router manufacturers all point fingers claiming their implementation of N speeds is perfect and everyone else is wrong! Your complaint:> only that wireless connection is connected however does not allow me internet access. ...is *the* classic 11n_disable symptom.

---

