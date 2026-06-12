---
title: "should i buy atheros or acx?"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by tempo500 on 2006-06-20
my netgear wg311v2 pci just got to a bit too hot....needs a total reboot to work another 15 minutes....
i have the choise between netgear(again :-/) or dlink. could someone give some advice on this? i checked

[http://linux-wless.passys.nl](http://linux-wless.passys.nl)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

my local stores have the 
netgear atheros - wpn311, wg311t, wg511t

d-link atheros - dwl-g510, dwl-g520

right now i think i am going to get the wg311t. i would like to avoid the acx chip because i had to load a old firmware on dapper to get going. so maybe... i am lucky and can get one that just works out of the box. thanks for any input, philip

---

### Post by meng on 2006-06-20
I think atheros is a good choice, although I don't know much about acx. For me it worked right out of the box (DLink DWL-G520). Of course, certain manufacturers (Linksys) have been known to sell the same model with different chipsets over time ...

---

### Post by noname101 on 2006-06-20
I have the same card and I use ndiswrapper. The acx driver is buggy. I wouldn't recommend another acx card. I'd get one of the atheros chipsets.

---

### Post by The Mad Scientist on 2006-06-20
I have not managed to get my DWL-G520 to work on 6.06 yet.  On 5.10, I had to go to a fixed IP address, as DHCP did not work.  This is probably the reason network manager is not working.  However, if you don't care about security, you shouldn't have any difficulties.  I only had the problems when I tried to get WPA-PSK working.

Yes, I have read the guides on how to compile your own driver to get it to work.  Unfortunately, at this time, the components they use are all newer than what is in 6.06, leading to a cascade of beta software that I really did not want to deal with or maintain.  There is a lot of activity going on right now.  This is probably a temporary problem, since the madwifi guys are making great strides.  It just isn't there quite yet...

---

### Post by Agent86 on 2006-06-20
I think that Atheros and ACX are (relatively) simple to get going in Dapper, as long as you don't need WPA. My ACX-based Netgear WG311v2 just needed minor edits to /etc/modprobe.d/options and /etc/network/interfaces and it was up and running.

Getting WPA working, on the other hand, was an "educational"  process :rolleyes:

---

### Post by tempo500 on 2006-06-21
great thanx for the reply! i will get the wg311T atheros chipset.... hope it will last this summer + the hardware manufactures get their stuff together for linux!

---

### Post by tempo500 on 2006-06-21
sooooo..... back from the store with a d-link dwl-g520 - atheros chipset. works out of the box with dapper. well since im now longer online than 15 minutes (overheated netgear card) i will write it again. - w o r k s   o u t   o f   t h e   b o x -
i am using wep because i am anyway restricting the wireless cards to the mac adress. so i guess this security level should be enough for now.

thanx to the people replying!! this went really easy. phil:KS

---

