---
title: "Broadcom wlan wireless help-beginner"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by EZasPi on 2010-02-26
Hi. I am new to linux and would appreciate some help getting my wifi working.
I have been looking around the internet for a while help, but with no success.
Here is some info:

I have a broadcom wireless card, model: BCM4306 802.11b/g Wireless LAN Controller
I have gotten the driver for this card installed, using ndiswrapper, successfully, I think.

In the Network-Manager, my wi-fi network is recognized, and then when I try to connect, it asks for my password, waits a while, then says that I am disconnected.

Just instruct me  to give you whatever information that might be helpful.

Thanks

---

### Post by pastalavista on 2010-02-26
> **EZasPi said:**
> Hi. I am new to linux and would appreciate some help getting my wifi working.
I have been looking around the internet for a while help, but with no success.
Here is some info:

I have a broadcom wireless card, model: BCM4306 802.11b/g Wireless LAN Controller
I have gotten the driver for this card installed, using ndiswrapper, successfully, I think.

In the Network-Manager, my wi-fi network is recognized, and then when I try to connect, it asks for my password, waits a while, then says that I am disconnected.

Just instruct me  to give you whatever information that might be helpful.

Thanks


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

Pay special attention to the part about blacklisting the open source drivers.

---

### Post by bkratz on 2010-02-26
> **EZasPi said:**
> Hi. I am new to linux and would appreciate some help getting my wifi working.
I have been looking around the internet for a while help, but with no success.
Here is some info:

I have a broadcom wireless card, model: BCM4306 802.11b/g Wireless LAN Controller
I have gotten the driver for this card installed, using ndiswrapper, successfully, I think.

In the Network-Manager, my wi-fi network is recognized, and then when I try to connect, it asks for my password, waits a while, then says that I am disconnected.

Just instruct me  to give you whatever information that might be helpful.

Thanks




Is your access point encrypted, and if so can you temporarily open it up, just long enough to see if you can connect?

---

### Post by EZasPi on 2010-02-26
I think that I did blacklist the old drivers correctly. Following the instructions in the link, in Device Manager the value for info.linux.driver is ndiswrapper.

I believe that my access point is encrypted, though i'm not sure, and I don't wouldn't know how to open it up to see if I can connect.

Thanks for replying.

---

### Post by pastalavista on 2010-02-26
I don't know much about ndiswrapper. It is an old workaround. Have you tried installing the open source 'b43-fwcutter' driver? It works fine on my sons Broadcom. Can you connect to the internet via ethernet cable? The Hardware Drivers tool in the System|Administration menu should offer automatic installation of b43-fwcutter.

---

### Post by EZasPi on 2010-02-26
I haven't tried connecting via ethernet yet. I'll do that and check out the b43-fwcutter driver. I'll post how that goes.

---

### Post by pastalavista on 2010-02-27
Hope it works. Don't forget to undo the blacklist before you try it.

---

