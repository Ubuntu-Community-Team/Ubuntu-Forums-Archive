---
title: "WG111T latest Drivers."
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by TimPy on 2009-06-13
Hi.  I was looking for the WG111T latest windows drivers.  From Netgear's website, I can get the [latest 2.1 drivers]("http://kb.netgear.com/app/products/model/a_id/2559").  However, They are wrapped in a .exe and not a .zip or anything.  According to the [hardware support wiki page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB"), this model is supported with the latest drivers and ndiswrapper.

I can run the .exe through wine, but I need to extract the driver's .inf and other files for ndiswrapper.  Can someone provide me with either just the latest drivers or a way to extract all the files I need from the "C://" drive of WINE? If I can get them, I'll provide them as an attachment here for other users to easily download... That way, others won't have to have the same problems I'm having.

... If only I hadn't lost the driver cd in the first place. *sigh*

Thanks.

P.S. - Just so you know, I can connect with the oldest drivers (the ones in a .zip), but only stay connected for around 5 seconds....

---

### Post by foxy123 on 2009-06-13
> **TimPy said:**
> Hi.  I was looking for the WG111T latest windows drivers.  From Netgear's website, I can get the [latest 2.1 drivers]("http://kb.netgear.com/app/products/model/a_id/2559").  However, They are wrapped in a .exe and not a .zip or anything.  According to the [hardware support wiki page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB"), this model is supported with the latest drivers and ndiswrapper.

I can run the .exe through wine, but I need to extract the driver's .inf and other files for ndiswrapper.  Can someone provide me with either just the latest drivers or a way to extract all the files I need from the "C://" drive of WINE? If I can get them, I'll provide them as an attachment here for other users to easily download... That way, others won't have to have the same problems I'm having.

... If only I hadn't lost the driver cd in the first place. *sigh*

Thanks.

P.S. - Just so you know, I can connect with the oldest drivers (the ones in a .zip), but only stay connected for around 5 seconds....

if you run the driver with wine the files you need are in ~/.wine/drive_c/Program Files/NETGEAR/WG111T/Driver I have attached the as well...

---

### Post by TimPy on 2009-06-13
Thanks.  That *almost* worked like a charm.

I was told I also needed a .bin file that you did not include; I'll include it in the attachment I will have.

*Note* For those following along, I also had to run 
```
cd /Directory/to/netwg11t.inf
sudo ndiswrapper -i netwg11t.inf
sudo modprobe ndiswrapper
```
before I could run the drivers properly.  Also, although many other tutorials that I have read suggested installing a athmwdl.inf 'bootloader' or something... It seems to be unnecessary in the newest drivers.

Good luck to anyone else following along! I plan on linking this for people who have lost their CD drivers too.  Seems to work like a charm now. Thanks again foxy123.

---

### Post by redneckincali on 2009-12-16
Hi I need the most current drivers for my Netgear WG111T USB Adapter.


Thank you.

---

