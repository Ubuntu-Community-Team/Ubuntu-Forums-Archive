---
title: "Linux compatible USB Wireless ?"
date: 2012-04-01
forum: Networking &amp; Wireless
---

### Post by lz1dsb on 2012-04-01
I was just thinking about buying a USB 802.11n Wireless card for my laptop. It seems like there's a lot of choice out there but as always the Linux support isn't exactly clear. 
I'm thinking about two models:
1. Edimax 7718Un
2. Linksys WUSB600N
It seems to me that this page is quite old. At least concerning the above mentioned models:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

So, has anybody in this forum used one of this two? Any thoughts about compatibility, issues etc.
And, oh yes, not to forget. I'm using Ubuntu 11.10 with kernel 
3.0.0-17.

---

### Post by josephmills on 2012-04-01
I have nothing but good things to say about these cards 
[http://www.google.com/products/catalog?q=alfa+wireless+cards+linux&hl=en&client=ubuntu&hs=Emn&channel=cs&prmd=imvns&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&biw=1313&bih=635&um=1&ie=UTF-8&tbm=shop&cid=10902005532878005520&sa=X&ei=gcN4T9mKDcbu0gGqscDTDQ&ved=0CLkBEPMCMAM](http://www.google.com/products/catalog?q=alfa+wireless+cards+linux&hl=en&client=ubuntu&hs=Emn&channel=cs&prmd=imvns&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&biw=1313&bih=635&um=1&ie=UTF-8&tbm=shop&cid=10902005532878005520&sa=X&ei=gcN4T9mKDcbu0gGqscDTDQ&ved=0CLkBEPMCMAM)


sorry that I can not say that I have used the other ones.

---

### Post by lJ9%3MR&gt;sa on 2012-04-01
The Edimax has a Ralink 2870 chipset. So it is completely compatible with Ubuntu. Just plug in and go. I would also like to recommend getting a D-Link DWA-125. It also has a Ralink 2870 chipset and gets great range.:p

---

### Post by lz1dsb on 2012-04-02
[QUOTE=faxmanloveswaffles;11810650]The Edimax has a Ralink 2870 chipset. So it is completely compatible with Ubuntu. Just plug in and go. I would also like to recommend getting a D-Link DWA-125. It also has a Ralink 2870 chipset and gets great range.:p
Could you confirm that it's working with 11.10. The information I've got from this site:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)
is probably a bit old, but it says that DWA-125 has "flaky" support in Ubuntu/Linux.
What would you say about DWA-140? Isn't it a better choice, from compatibility perspective off course...


Boyan

---

### Post by lz1dsb on 2012-04-02
Isn't that great?!! 
I've just bought a DWA-131 USB Wireless adapter from D-link and it just worked out of the box :lolflag:
Exactly like it's written on the Ubuntu page (the very last line in the table there):
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

And I can even use the 13-th and the 14-th channels which are not allowed with the STA Broadcom driver for my embedded wireless :guitar:

I'll continue working with the device throughout the week and will share my experience. So far it looks promising...

---

### Post by kurt18947 on 2012-04-02
I have a Dlink DWA-131 as well.  It uses a RealTek rtl8192SU chip that had a somewhat difficult Ubuntu birth but works well now.  Another nice choice is the Edimax 7718Un that uses a Realtek 8188Cus chip.  It's not plug like the Dlink but the RealTek driver has an install script that makes it easy to install.  The benefit of the 'nano' adapters is that they only protrude from a USB port about 1 cm. or less and my range & throughput are very good.  I did find it necessary to blacklist the native driver in Mint 12 when using the Edimax.

---

### Post by lz1dsb on 2012-04-03
I also noticed that when I suspend or hibernate my laptop, the WiFi USB adapter isn't recognized after that. I have to plug it off and back on again and it's immediately recognized by Network Manager. Strange. I don't know if it has to be that way, but it works for me...

---

### Post by lz1dsb on 2012-04-05
I've been happily using DWA-131 for few days now. And I could say that the compatibility with Ubuntu/Linux looks quite good. So I'm marking this thread as closed.

---

### Post by kurt18947 on 2012-04-06
> **lz1dsb said:**
> I also noticed that when I suspend or hibernate my laptop, the WiFi USB adapter isn't recognized after that. I have to plug it off and back on again and it's immediately recognized by Network Manager. Strange. I don't know if it has to be that way, but it works for me...

Yes, I noticed the same thing re suspend/hibernation.  The problem is that the wifi adapter needs to suspend before the systems goes into suspend.  The fix is:

```
sudo gedit /etc/pm/config.d/config
```

a blank page will open. Enter this one line and save.

```
SUSPEND_MODULES="r8712u"
```

Thanks to chili555 for this solution.

---

### Post by lz1dsb on 2012-04-06
Sounds rather interesting. I do have to give it a try tomorrow. Today I'm on the road and I don't have access to my Ubuntu laptop.
Thanks for sharing!

---

### Post by lz1dsb on 2012-04-07
> **kurt18947 said:**
> Yes, I noticed the same thing re suspend/hibernation.  The problem is that the wifi adapter needs to suspend before the systems goes into suspend.  The fix is:

```
sudo gedit /etc/pm/config.d/config
```

a blank page will open. Enter this one line and save.

```
SUSPEND_MODULES="r8712u"
```

Thanks to chili555 for this solution.

That's amazing! I don't know what I did exactly, but it works exactly as you say! Thank you! And also we have to thank also chili555 for providing the solution!
It's so nice that I can fully control the USB wireless card directly from the Network Manager :guitar:

---

### Post by fresnofred on 2012-04-08
i would purchase from ebay an airlink101 model 3026 usb wifi device.  they work great with just about any linux system.  i am not familiar with the devices u mentioned but have used the airlink101 model noted above with GREAT success.

---

### Post by reachcontrol on 2012-04-20
> **lz1dsb said:**
> That's amazing! I don't know what I did exactly, but it works exactly as you say! Thank you! And also we have to thank also chili555 for providing the solution!
It's so nice that I can fully control the USB wireless card directly from the Network Manager :guitar:


Same problem, solution worked perfect!

I now have a fully functional Ubuntu laptop to play with.

Thanks!

-R

---

