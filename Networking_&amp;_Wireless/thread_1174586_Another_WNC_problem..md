---
title: "Another WNC problem."
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by damo566 on 2009-05-31
[This may have already been posted. If so, I'm sorry for wasting your time.]
I'm running Ubuntu 7.10, and I've been wanting to switch to a wireless connection for a while now, instead of being stuck in one place with an e-cable. So I looked up a few sites that told me to do this:
sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid “essid”
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]
I like to think that I know what I'm doing, but that only ended with  "No DHCPOFFERS received. No working leases in persistent database - sleeping."
SO.
I looked further down the page, and found something about an encrypted connection (our router) that said:
sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [inteface] essid “ESSID_IN_QUOTES”
sudo iwpriv [interface] set AuthMode=WPAPSK
sudo iwpriv [interface] set EncrypType=TKIP
sudo iwpriv [interface] set WPAPSK=”YOUR_WPA_PSK_KEY”
sudo dhclient [interface]
BUT. When I enter "sudo iwpriv wlan1 set AuthMode=WPAPSK" it complains that Set is not a valid command.
So, what is?
[If it helps, my card is an Alloy GL242201, my router a Linksys Wireless-G.]

---

### Post by superprash2003 on 2009-05-31
lets start over , in your terminal type **lshw -C network** and post output

---

### Post by damo566 on 2009-06-01
Argh, can't D:
I've discovered that nothing loads while the card is plugged in; no terminal, no response if it's already open, etc etc.
Damn.

---

