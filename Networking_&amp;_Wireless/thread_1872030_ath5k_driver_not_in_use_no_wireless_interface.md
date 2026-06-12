---
title: "ath5k driver not in use no wireless interface"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by sarmadzhiev on 2011-10-29
Hi all,

I have just upgraded my system to 11.04 and the wireless stopped working

Network card: Arthoes AR5001

kernel module is loaded (ath5k)

lsmod shows ath5k 
lspci -k -nn 
shows for the card, 
   kernel modules: ath5k

but does not say its in use. 

Wireless alias used to be ath0, and ath-pci is blacklisted

lshw -C network shows
*-network:0 UNCLAIMED
and the description for ar5001x+ wireless adapter does not show localname for example

On boot it did not load ath5k either, 
until I forced it in /etc/modules by adding 'ath5k'
Also, sometime during boot, I see a message ath5k fails to obtain pci memory or something. but it loads anyway.

lsmod | grep ath5k 
ath5k 
ath        xxxxx ath5k
mac80211   xxxxx ath,ath5k
cfg80211   xxxxx mac80211,ath5k

Any help will be appreciated. I moved the desktop to a room without wired Internet, and now I am puzzled how to use it.

---

### Post by sarmadzhiev on 2011-10-30
I found the issue. It was irq resource mess up. I switched off the conflicting card and now the driver is working. thx, mark it as resolved.

---

