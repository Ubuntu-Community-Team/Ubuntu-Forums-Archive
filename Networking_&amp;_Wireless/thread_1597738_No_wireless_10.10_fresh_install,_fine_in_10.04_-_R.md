---
title: "No wireless 10.10 fresh install, fine in 10.04 - Realtek"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by TBABill on 2010-10-15
I installed 10.10 from a clean, good md5sum, slow burn, etc etc. Install was flawless and I managed to connect to the net via ethernet. However, the wireless is enabled in the network manager and it sees my network. However, it prompts for the WEP key and tries over and over to connect. It works fine on 10.04 and it sits less than 15 feet from the router. 

Any idea what changed for a card that is automatically detected in Karmic and Lucid, and appears to work with Maverick but will not connect? Suggestions? I have seen many posts of various cards failing to connect in Maverick that worked in 10.04, but the only successful fix I found in the forums was a BIOS upgrade. I'm not taking that step for what looks like a regression.

Similar thread here but the solution is in German so I'm a bit out of luck: [http://ubuntuforums.org/showthread.php?t=1590415](http://ubuntuforums.org/showthread.php?t=1590415)

---

### Post by plizzba on 2010-10-30
I am also having this problem :(

I have this card: (output from lspci)
> 01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

There is a bug at [http://ubuntuforums.org/showthread.php?t=1590415](http://ubuntuforums.org/showthread.php?t=1590415)
which applies to my card.

---

