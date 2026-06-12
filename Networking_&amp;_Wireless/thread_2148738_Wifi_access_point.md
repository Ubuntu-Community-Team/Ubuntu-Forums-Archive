---
title: "Wifi access point"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by yucapsiho on 2013-05-26
Heloo everyone.   

So lets go whit the question. I have bin trying to make my wifi adapter a AP. Actuality a was reading a lot about all the staff that go's whit this. After a lot of time spent on reading a went and check my hardware if this is possible. I am on ubuntu 12.4 LTS 32xbit, karnel 3.2.0-44-generic-pae and my wifi card is intel corporation centrino wireless-n 1000 bgn 
My iw list command output is: 

... Supported interface modes:
              *IBSS
             *managed
             *monitor
  software interface modes (can always be added):
        *monitor 
interface combinations are not supported 
.....    

so probably this is it for my wifi adapter or is it?   

I am thinking of baying new hardware that will make this possible. If anyone has any suggestions please let mi know.  Is it safe and will hostapd support this 
physical cable--->dhcp server--> usb Wifi adapter ---via Wifi--->to devices

  And so I clarify I do not wont any ad-hoc connection or any thing like that. I wont to have a safe secure wifi connection in my home for all devices in use and in need of Internet connection.  So that the  
physical cable--------->dhcp server------via Wifi------>to devices. 

Thanks a bunch.

---

### Post by scbingham on 2013-05-26
Plenty of info if you search for it.

This looks easy enough: [http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)

---

### Post by yucapsiho on 2013-05-26
A made it perfectly clear I do not wan to ad-hoc.  
 

 I wan to know are there any usb adapters that support hostapd if not what wifi cards are a good solution for mi?

---

### Post by scbingham on 2013-05-26
I missed the bit about ad-hoc. I tried the example & it didn't actually work for me.

Maybe you too will have to do some research, as will I.

---

### Post by scbingham on 2013-05-27
Using hostapd & dnsmasq, as described in this article, looks like the way forward:

[http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/](http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/)

---

### Post by prodigy_ on 2013-05-27
> **yucapsiho said:**
> 
Supported interface modes:
              *IBSS
             *managed
             *monitor
The AP mode isn't listed, which is strange because Wireless-N **1000** should indeed support it. Are you sure it's not Wireless-N **100**?

---

### Post by yucapsiho on 2013-05-27
Jep my lshw for network:

 *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000 [Condor Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 00
                serial: 74:e5:0b:03:fa:ae
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-44-generic-pae firmware=39.31.5.1 build 35138 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:43 memory:f1a00000-f1a01fff

---

