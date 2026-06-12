---
title: "b43 driver loses wifi connection"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by snif123 on 2010-08-16
HI all
I have been puzzled by a driver issue for days now.I am using the B43 STA driver for my BCM4312 card in LUCID 10.04.This works fine.But everytime I change over to the b43 driver,the wifi connects and when I open a browser,it disconnects and attempts to reconnect in vain.Is this driver OK to work on this kernel?I want to use this because it supports monitor mode for my card
2.6.32-24-generic
Cheers

---

### Post by bkratz on 2010-08-16
> **snif123 said:**
> HI all
I have been puzzled by a driver issue for days now.I am using the B43 STA driver for my BCM4312 card in LUCID 10.04.This works fine.But everytime I change over to the b43 driver,the wifi connects and when I open a browser,it disconnects and attempts to reconnect in vain.Is this driver OK to work on this kernel?I want to use this because it supports monitor mode for my card
2.6.32-24-generic
Cheers

Well it depends on which version of the 4312 you happen to have.
If yours is the

BCM4312    ID #14e4:4315  it is supported by b43 in a later kernel, below is from the page mentioned.
supported [COLOR="Red"]2.6.33[/COLOR] and later (PIO mode)

See this page for more info

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by snif123 on 2010-08-17
Hi
Yea unfortunately that is the ID..14e4:4315 so I will have to have move up to a newer kenel.
Thanks for that,you have confirmed my fears :D

---

