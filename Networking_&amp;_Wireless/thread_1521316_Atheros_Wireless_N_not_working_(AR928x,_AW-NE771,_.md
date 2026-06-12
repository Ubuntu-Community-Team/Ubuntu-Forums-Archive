---
title: "Atheros Wireless N not working (AR928x, AW-NE771, AR5B91, AR5B91-X)"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by Timothy Benton on 2010-06-30
I just got a bunch of new parts for my PC. This is the motherboard I bought (ZOTAC H55 ITX):
[http://www.anandtech.com/show/2950](http://www.anandtech.com/show/2950)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500043&Tpk=zotac%20h55](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500043&Tpk=zotac%20h55)

It has a built in AzureWave AW-NE771 wireless N PCI Express card, which uses the Atheros chip model number AR5B91-X. In Windows it shows up as AR928x and works okay. But I tried Ubuntu 9.10, 10.04, 10.10 Alpha 1, Fedora 13 and OpenSuse and none of them even recognize the wireless card. Other people have said it works out of the box, but on my computer it isn't detected. I tried going in the Restricted Drivers thing and all I saw was my graphics card (GeForce 8800 GTS 512). I tried to install MadWifi and ath9k, but I couldn't figure it out. I might try NDISwrapper but I'd rather not if there is a native Linux driver.

I can't use Synaptic on the computer because it is not connected to the internet. No driver. But I can download files to a USB from my laptop.

Any ideas? Thanks in advance

----------------------------

Solved. It was some BIOS setting, a BIOS reset fixed it. If your ZOTAC H55-ITX wireless isnt working try resetting your bios.

----------------------------

Upon further investigation I found I had disabled all the PCI-Express slots. Don't know how my graphics card still worked or why the wireless still worked in windows

---

