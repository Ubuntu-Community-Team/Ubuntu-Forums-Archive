---
title: "/etc/interfaces file only has loopback"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by respeseth on 2009-10-16
I think I'm in over my head. Trying to get wireless to work on a Dell with the Broadcom card. Ran command lshw -C network, show wireless card as disabled. Ran command ifup eth0, eth1 and wlan0...unknow interface error. Took a look at the /etc/networks/interface file and it only has the loopback. Do I need to edit interface and if so what should it look like? If not what's not set correctly. To me it appears that the card driver is loading.

Thanks

Bob

---

### Post by amingv on 2009-10-16
Don't edit /etc/network/interfaces unless you're planning to manage the network connection *entirely from the command line*.
Most network managers won't manage the network if you edit interfaces, and it's OK for it to have only loopback.


When you did lshw, did the card come up as unclaimed? Can you see the card (or any available networks) on the network manager?

---

### Post by respeseth on 2009-10-16
No the wireless card is shown as disabled. This makes me think that the driver is correct.
This Dell Laptop has a wireless symbol above the F2 key with a function shift. My other dell has a hardware switch to enable / disable the wifi. This laptop does not understand the notion of enabling  /disabling the wifi from the softkey. I believe this to be true because several of the other softkey seem to work correctly, like the F3 battery or the F8 CRT/LCD. Not sure how to get the wifi turned on.

---

### Post by amingv on 2009-10-17
If you suspect the switch is failing to bring it up, you may want to check in the BIOS to see if you can enable it manually from there (there's nothing to loose by trying).
At least we'd be able to discard that possibility.

---

### Post by respeseth on 2009-10-17
Thanks to all that offered help. Decided to start over, reloaded from the CD, ran fwcutter, now the WIFI symbol is illuminated (all be it all the time) so it does not show true state of wlan. Dmesg does tell true state. We are now wireless. Again Thanks

Bob

---

