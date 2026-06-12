---
title: "How do I configure detected wireless card?"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by heislord5 on 2006-03-12
Hi,

I used synaptic package manager to install linux-wlan package so my card can be recognized.  

iwconfig shows the following output:

IEEE 802.11-DS ESSID:"2WIRE015" Nickname:"2WIRE015"
Mode:Ad-Hoc Frequency:2.412 GHZ Cell:.....
Bit Rate:2 Mb/s Tx-Power:18 dBm
Retry min limit:8 RTS thr:off Fragment thr:off
Encryption key:off
Link Quality=4/92 Signal level=-95dBm Noise level=-100 dBm
.........

Where do I go to set all these parameters to what I want.
My wireless network is encrypted and I need to add the encryption key and I also might need to change from ad-hoc, because I don't know if that is what I have.  I have (in windows) set to any with infrastructure preference.

Does anyone know where the file is that I have to change?

I can't do it through the network menu.  It doesn't have boxes to set network key or mode.

please help.

Brad

---

### Post by heislord5 on 2006-03-12
configuration is done in the interfaces file:
/etc/network/interfaces

I have it set to managed as it should be.  Now everything is correct except it won't use encryption.

I disable encryption (from the router) and I can get on the internet, but as soon as I turn my router's encryption back on, it doesn't work!

Obviously ubuntu is configured for nonencryption, but I have the encryption code in the interfaces file.

My interfaces file is like this (fake key number of course):

iface wlan0 inet dhcp
wireless-essid 2WIRE015
wireless-mode Managed
wireless-key 0123456789
auto wlan0

now that works fine if modem encryption is off.  It just ignores it.  But if modem encryption is on, it still ignores it.  So it can't communicate on the network.  What setting am I missing to tell it to use encryption.  I'm fairly sure it belongs in this file.  Is there anywhere where there is a list of all the possible parameters I could pass for wireless-XXXX?

Thanks

Brad

---

### Post by trorion on 2006-03-13
By default the encryption information is in hex format so you'll need to convert to hex format OR

System -> admin -> networks
You can enter the info there.

---

