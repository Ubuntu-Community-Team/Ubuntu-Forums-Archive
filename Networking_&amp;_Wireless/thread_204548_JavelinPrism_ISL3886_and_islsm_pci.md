---
title: "Javelin/Prism ISL3886 and islsm_pci"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by matc on 2006-06-27
When I used breezy, I had my wireless MiniPCI-device controlled via ndiswrapper and it worked somehow.
Now I upgraded to dapper and installed kNetworkManager. It seems that the control via ndiswrapper has been replaced by islsm_pci, which succeeds in finding network but can't connect even to unencrypted ones. Trying this via kNetworkManager makes the device hang at 28%. 

My questions:
- How to get islsm_pci working? Do I need firmware for this? If yes, where?
  Is there some documentation on this topic (haven't found much helpful stuff)
- How to work with wpa_supplicant? 

lshw states:
           *-network:0
                description: Wireless interface
                product: ISL3886 [Prism Javelin/Prism Xbow]
                vendor: Intersil Corporation
                physical id: 1
                bus info: pci@01:01.0
                logical name: eth2
                version: 01
                serial: 00:90:4b:d9:be:0e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=islsm_pci multicast=yes wireless=IEEE 802.11b
                resources: iomemory:e0002000-e0003fff irq:11

---

### Post by Dr. Nick on 2006-06-27
Try [here]("http://ubuntuforums.org/showthread.php?t=198192")

Just had a nice discussion on this topic, I think the easiest solution is to remove islsm_usb and go back to ndiswrapper. The soultions come around pg 4 or so, Any questions just ask back here

---

### Post by matc on 2006-06-27
That's the worst thing to do because the windows drivers I got work crappy with the wireless device (~170 kB upload/outgoing...)

1. Why on earth did the dapper update "update" the WLAN drivers and leaving them in such a inconsistent state without even telling the user there have been changes on this subject ???

2. Why on earth do we use drivers nobody knows how to use ??? Do they work at all??

---

### Post by Dr. Nick on 2006-06-27
[quote=matc]That's the worst thing to do because the windows drivers I got work crappy with the wireless device (~170 kB upload/outgoing...)

1. Why on earth did the dapper update "update" the WLAN drivers and leaving them in such a inconsistent state without even telling the user there have been changes on this subject ???

2. Why on earth do we use drivers nobody knows how to use ??? Do they work at all??[/quote]


I dont have your exact card, but have a similar situation with my card.

Each kernel update will load all the newest drivers, you will hit this problem with every linux distro, not just ubuntu. Alot of these drivers are made by 3rd parties and have their own means of configuration, I can get the drivers to work for my card but it involves a bit more work editing files and whatnot.

The drivers may work, just may be more of a hassle then it is worth for some people,


If you cant find a document helping you get the islsm ones working ndiswrapper may be the best choice :( Sorry I dont have the same card to help you. Just rememberd a similar situation with another user that got his card going good with ndiswrapper

---

### Post by matc on 2006-06-28
Ok I reverted to ndiswrapper. But somehow there are no wpa_supplicant startup scripts any more. How do I run and confgure it now?

---

### Post by Dr. Nick on 2006-06-28
Sorry I have no idea on wpa_supplicant, hopefully someone else has your answer

---

### Post by matc on 2006-07-03
Happiness!

wpa_supplicant issue is solved. Didn't know that /etc/Network/interfaces now invokes the wpa_supplicant with

wpa-conf /etc/[conf-file].

Wireless now works via ndiswrapper, WPA-PSK and surprising 1MBps Upload (on breezy I got less than 200KBps)...

---

