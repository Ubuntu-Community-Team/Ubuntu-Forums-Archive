---
title: "Super Slow Wireless RaLink RT2500"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by jackwhite on 2010-02-27
hi folks,

My wireless on my Ubuntu desktop is really slow compared to my windows laptop. Its not a flash problem or a browser specific problem.

I have searched the forums but can't find much. 

I did disable ipv6 (it now shows up as being 'ignored' in network Manager which is correct, right?) but that hasn't helped.

It doesn't make a difference whether I use DHCP for everything or just for address only with the Google DNS addresses.

Any further advice or tips?

After entering 'lspci' my card shows up as ```
RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
```

Because of a problem with system freezes I have updated to the 2.6.33-020633rc7 kernal but this hasn't had any impact one way or another on wireless speeds.

My router is a Belkin WRT300n.

---

### Post by jackwhite on 2010-02-28
well this has been a nightmare.

To anyone else who comes accross this post theres a lot of solutions out there. They're easier to find using google than the search on Ubuntuforums but most of them are threads on Ubuntuforums.

Theres one where you set the MB rate - didn't work for me.
Theres one where you install WCID and then set the aate -didn't work for me.
Finally theres one where you install rt2500.inf with ndiswrapper. This didn't work for me.

any help out there?

---

### Post by pazsion on 2010-07-17
having issues too...bump bump

---

