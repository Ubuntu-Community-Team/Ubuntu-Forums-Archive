---
title: "CAN connect with Netgear wpn511"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by janusm on 2008-12-28
My computer is a IBM T30 and running Ubuntu Hardy Heron, 8.04.
Here is what I did after trying for quite some time to get my wireless card to work.  I found this on some Linux website, and it WORKS !!!!!!
In my T30, I had to remove my internal WiFi card.

1. Plugged in my netgear WPN511 card.  It started flashing 2 light alternately.
2. (Applications, Assessories, Terminal) Typed in:
sudo iwconfig atho essid <your ssid here>
sudo iwconfig ath0 key <your hex key here> restricted
sudo iwpriv ath0 mode 3
sudo iwpriv ath0 authmode 2
sudo dhclient ath0
3. After the second iwconfig, both lights started blinking together.
4. I could login to my website.

I had another Netgear card, WG511U and that works too.

At the moment I have to write these instructions everything time the computer is booted. I have a question, where do I put these instructions to automatically when booted it is included.

-Jan

---

