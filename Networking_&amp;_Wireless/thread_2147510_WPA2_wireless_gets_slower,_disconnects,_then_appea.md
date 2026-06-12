---
title: "WPA2 wireless gets slower, disconnects, then appears as WEP, cant connect"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by veroslav on 2013-05-22
Hi,

I am having the following setup:

A Dell Laptop running (K)Ubuntu 12.04/Windows 7 and a HP Destop running Kubuntu 12.10/Ubuntu 12.04/Windows 7.
Both computers are connected wirelessely to my router. The connection is WPA2 secured.
The router is a D-Link DIR-615.

Laptop wireless:
Unfortunately I dont have access to the hardware specs for this one at the moment, but I do know that it has a wireless chip from Atheros (I will gladly provide more details if needed) and normally it works beautifully.

Desktop wireless:
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:2a9c]
    Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Lite-On Communications Inc Device [11ad:6632]
    Kernel driver in use: rt2800pci
```

The issue (happens on both the laptop and the desktop):

Sometimes, mostly during heavy downloading, the wireless first gets very slow. Normally I max out 10 Mbit/s, but during the slowdown I get somewhere around 3 Mbit/s at most. Browsing the Internet is very slow too.

A while after a slowdown, it either disconnects or I am unable to connect after a reboot, if I still happen to be connected when I shutdown. 

When I get disconnected, if I try to connect again, my wireless is shown as WEP protected, and not WPA2 protected anymore! At this point I never manage to connect, as my password is too long to be accepted as a WEP password. If I reboot into Windows 7, it appears as WEP protected there as well and I can't connect!

Now, if I login into the router as admin when this happens, the connection details for my connection are shown correctly (WPA2 security and my original password). Changing password/ssid/security does not change anything; the connection is permanently shown as WEP-protected and I am unable to connect to it.

This is what I've tried to solve the problem (nothing worked):

Remove all the connections from the network manager.
Add new wireless connection manually
Disable/Enable wireless/network
Remove/add network manager applet

The only thing that helps is resetting the router to the default configuration. Even at this point, the connection can be very slow to begin with, and it usually takes a few router restarts to get it "up to speed".

This happens once every 1-2 months or so on average but it is very frustrating when it happens.

I am wondering where to begin debugging? I am suspecting something in the router but I am not well versed in this area. Wired connection works ok at all times.

Anyone who can shed any light on this strange issue? How would I approach it when/if it happens again?

Thanks in advance.

Kind Regards,
Veroslav

---

### Post by praseodym on 2013-05-22
For the desktop with Ralink chip, install this driver:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5561332](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5561332)

For the Atheros chip, deactivate the hardware encryption, e.g. for the module ath9k
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by veroslav on 2013-05-22
Thank you for your reply, praseodym.

Could you please elaborate a bit on the reason behind installing the new Ralink driver and also what does the hardware decryption for Atheros chip does?

I would just like to be sure of what I am going to do exactly.

Also, I want to stress that my wireless can be up and running for days/months without any issues on both Atheros and Ralink, that is why I am curious as to what changes I can expect from following your instructions.

Thanks again.

Regards,
Veroslav

---

### Post by praseodym on 2013-05-22
The (additional) hardware encryption slows down the connectivity, WEP/WPA encryption is not affected by this, so the network is still safe.

The native driver rt2800pci is still not stable enough for this card. Therefore, it can/should be replaced by the driver from the supplier. It has to be mentioned that the Ralink driver needs to be compiled again after a kernel upgrade

---

### Post by veroslav on 2013-05-22
Thanks for the good explanation, I will have a look when at home.

If you would allow me to ask one more question, as you seem to be knowledgable in the subject:

How come Windows 7 is also affected (shows my wireless as WEP) after I reboot into it when the problem occurs? If I understood what you said correctly, it would appear that only the Linux drivers are affected and thus if there is any instability in those, they shouldn't have any impact on the Windows' ones right?

Also, perhaps less interesting but nevertheless, the first time I've got this WEP issue was 4 months ago. At that time my desktop was 2 years old and the laptop 1 year old respectively. During this time the only issues I experienced was an occasional disconnect which was quickly resolved by a router restart.

Perhaps there was a kernel update that messed something?

And one more thing: I have never upgraded router firmware since I bought it (ca 2 years ago). Is it possible that such an upgrade would be beneficial in resolving the WEP issue?

Thank you praseodym.

Regards,
Veroslav

---

### Post by praseodym on 2013-05-22
Yes, firmware updates of routers close security problems. I recommend changing also the wifi settings in the router interface

---

### Post by veroslav on 2013-05-27
Hi again,

I just wanted to say that the errors I was getting above might have been due to a faulty router. Last week it started frequently dropping the Internet connection and delivering VERY low speeds while still connected. I performed a firmware upgrade but that didn't help.

So I finally bought a new one and this one is working beautifully with both Ubuntu and Windows 7 so far. I also get much better signal and throughput.

Problem resolved!

Kind Regards,
Veroslav

---

