---
title: "Belkin G Plus Notebook Wireless Card"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by uxohus2b on 2006-07-13
Hi,
I'm trying to install a belkin wireless card (model no. F5D7011) on my laptop. I use Ubuntu 6.06. 

I followed the directions from this blog exactly:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=belkin+wireless+notebook](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=belkin+wireless+notebook)

Now, I at least get the power light to blink on my card, but the connectivity light never blinks, and the signal strength is zero when it should be very strong. 

Also, for some reason, when I open System > Administration > Networking and go to the configuration page for my wireless connection, the network name drop-down shows the available network connections ONLY at the very first time I try it after rebooting the machine. After that, the thing doesn't seem to recognize any of the availble connections--not, that is, until the next time I boot up.

This is what I get when I type iwconfig:


lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"standard"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I've looked at a bunch of howto's but I didn't find one that addresses my problems. Could someone please help? Thanks a lot. 

Regards,
hy

---

### Post by weekend warrior on 2006-07-14
No clue what's going on there but I can tell you that the [Belkin F5D7010]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136500") that I have works straight out of the box without any configuration. It's one of the good ones [listed at the FSF]("https://www.fsf.org/resources/hw/net/wireless/cards.html")

It's worth considering at least if you're toiling against the one you have. Just checked Ebay and there are 8 of them on auction right now, 2 of them are even right up the road from you, in New Jersey - both currently going for under 10 dollars I might add.

I know that's not the help you're looking for but it's just a thought.

---

### Post by uxohus2b on 2006-07-14
Thanks for letting me know. I'll have to resort to that if I can't fix the problem here.

---

