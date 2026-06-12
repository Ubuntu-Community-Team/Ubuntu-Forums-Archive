---
title: "Wireless stops working every few minutes, and starts working again?"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by ammarr on 2010-02-07
I need some help debugging this, so if someone could guide me a little bit.

I'm connecting to a wireless router (using WPA2) from my laptop and every few minutes my wireless connection stops working. It shows it as connected (I've tried both network manager and wicd) (so technically it doesn't 'disconnect'), but I can't ping sites or my router either. Then after a few seconds (around 30 seconds?) it starts working again without me having to do anything.

lspci shows me:

Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01).

System -> Administration -> log file viewer doesn't show me anything interesting at the times when the wireless stops working.

Other connected devices (iphone, android, another netbook running ubuntu 9.10) continue to work fine and without issues.

Any hints/tips on what I can do next? Kind of an annoying issue because it interferes with IM/video chat/streaming etc.

---

### Post by ammarr on 2010-02-07
Just to add some more info, this seems to happen when scanning for other networks. So it coincides with wpa_supplicant ctrl-event-scan messages in daemon.log and when manually refreshing available networks in wicd etc. Any tips on what I can do to fix this? Any way to disable scanning if I'm already connected?

---

### Post by ammarr on 2010-02-07
For others having the same issue: I think its a bug with the ath9k/5k drivers which causes your network to freeze everytime it does any scanning. I switched to using madwifi drivers using this guide: [http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/](http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/) and it seems to work fine now.

---

