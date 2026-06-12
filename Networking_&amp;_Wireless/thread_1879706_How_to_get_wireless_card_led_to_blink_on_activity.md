---
title: "How to get wireless card led to blink on activity"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by J0nDaFr3aK on 2011-11-12
Hi,
I installed Ubuntu 11.10 on my laptop a couple of days ago. What I noticed is that my wireless card LED (it's a atheros card, driver is ath9k) isn't blinking anymore on network activity. it did when I used windows on this machine (the blink frequency depended on the bandwidth, from slower to faster) and it kinda worked with Ubuntu 10.10 (though it would blink at the same speed, no matter what bandwidth speed). Now, with Ubuntu 11.10 it just stays on when the card is enable, it stays off when I power it off. I need it to blink, cause it gives me indication of the network speed, so I can see if the download speed is at its max speed or not.
I've searched everywhere, but I only found tips on how to disable the LED blink, rather than enable it.
can anyone help me please? thanks

---

### Post by chili555 on 2011-11-12
Please try this:```
sudo rmmod -f ath9k
sudo modprobe ath9k blink=1
```If it works, we can write a file and make it permanent.

---

### Post by J0nDaFr3aK on 2011-11-13
it worked like a charm, man! thanks a lot. so, what's the next thing to do? i mean, to make it permanent. thanks for the help, i appreciate it.

---

### Post by chili555 on 2011-11-17
Sorry I missed your reply. Here you go:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Add one line:```
options ath9k blink=1
```Proofread, save and close gedit. You should be all set.

---

### Post by J0nDaFr3aK on 2011-11-19
Thanks a lot. It worked!

---

### Post by chili555 on 2011-11-19
Please use Thread Tools at the top to Mark Solved.

Caution to the searchers: blink=1 is a parameter in some but not all drivers. Check your driver with *modinfo*:```
modinfo ath9k
filename:       /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7D3316A936D7C60FE66D883
alias:          platform:ar934x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,cfg80211,ath9k_common,ath
vermagic:       3.0.0-12-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
[COLOR="Red"]parm:           blink:Enable LED blink on activity (int)[/COLOR]
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
```If your wireless driver doesn't contain this or a similar parameter, this fix won't work for you.

---

