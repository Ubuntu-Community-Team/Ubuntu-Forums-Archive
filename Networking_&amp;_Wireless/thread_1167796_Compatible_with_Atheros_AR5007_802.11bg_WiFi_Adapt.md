---
title: "Compatible with Atheros AR5007 802.11b/g WiFi Adapter?"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by jt2009 on 2009-05-23
I've recently installed Ubuntu 9.04, deciding to give Linux another go. Always gave up before because I could never get wireless working (no internet = whats the point).

Ubuntu 9.04 Looks awesome and it actually detects my wireless card and can see the neighborhood networks (previous versions couldnt). So I am very excited about that.

The problem I am having is that my network is WEP2-AES and I can't seem to connect using Ubuntu. It keeps asking for the password.

I was able to connect 1 time for 2 minutes but it disconnected without any reasons and I havent been able to re-connect since.

I tried the alternate WiFi driver (madwifi) but no luck.

My network connections are restricted via device MAC addresses.

I've tried adding a new wireless connection using SSID & MAC address & WAP/WAP2 & password but no luck.

A strange thing I've noticed is that if I try connecting to my network several times it keeps adding a new connection entry to the wireless list. Is that normal? I have 2 dozen connections now name "Auto default"

any ideas?

Be gentle, I'm new to linux

thanks :p

---

### Post by jt2009 on 2009-05-25
anyone?

---

### Post by t0mppa on 2009-05-25
Well, to answer your first question, I have an AR5007 (Ubuntu lists the chip as AR242x though) that works just fine with ath5k on Jaunty and can connect to WPA2/AES.

Never ran into the trouble of being able to detect networks, but not connect to them. Do remember seeing threads about this on the forum and there's been some working fixes for the issue.

---

### Post by karesz on 2009-08-05
I'm having the same problem... Exactly the same. I hope we can find a solution soon. If i'll have some time, i'll try some of these forums advices:
[http://crunchbanglinux.org/forums/topic/3454/resolved-904-jaunty-wireless-wpa-not-connecting/](http://crunchbanglinux.org/forums/topic/3454/resolved-904-jaunty-wireless-wpa-not-connecting/)

[http://crunchbanglinux.org/forums/topic/702/resolved-no-network-connections-on-81002-inspiron-notebook/page/3/](http://crunchbanglinux.org/forums/topic/702/resolved-no-network-connections-on-81002-inspiron-notebook/page/3/)

[http://crunchbanglinux.org/forums/topic/3412/wpa2-networks-not-connecting-with-eee-901/](http://crunchbanglinux.org/forums/topic/3412/wpa2-networks-not-connecting-with-eee-901/)

Hope it'll help

---

### Post by MadHatter21 on 2009-08-05
I have proably posted this same reply 5 times now. The driver package that you can use is called ath9k. You can get it by going to google and typing in compatible wireless. Then download the 2.6.30 file and unzip it. After that run the following in the directory of the unzipped file.

Make 
sudo make install
sudo make unload

then restart your computer. Also add the ath9k to the modules list.

Sudo pico /etc/modules

add the line

ath9k 

Save and restart. This driver works for mostly all current atheros cards.

MadHatter21

---

### Post by drpjkurian on 2009-08-13
Hi Maadhutter
Well i was using hardy with a robust madwifi drivers for atheros card. well when i upgraded it to Kubuntu jaunty, my wireless failed. I tried to activate the propreitary drivers from system-> Hardware driver,but failed. well i also tried some thread which instructed me to install madwifi tools.

But all failed


with regards
Dr kurian


-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wifi0
                version: 01
                serial: 00:17:c4:39:f9:da
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

