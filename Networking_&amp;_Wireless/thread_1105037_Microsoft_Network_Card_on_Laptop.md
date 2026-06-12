---
title: "Microsoft Network Card on Laptop"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by SirScott13 on 2009-03-24
I have an old Dell CPt laptop that doesn't have an integrated network card.  When it was being used as a Windows machine, I used a Microsoft MN120 wired Network card.  Now that I have installed Xubuntu, I can't get it to work.  I am new to Xubuntu and Linux and don't know how to tell if the system has a driver loaded.  I have run lspci and I can see that it recognizes the card.  The chipset is ADMtek Centaur -C.  I have the driver available in a Windows version.  Any help would be appreciated.

---

### Post by chili555 on 2009-03-24
I believe this is supposed to work with the module called *tulip.* Please open a terminal and do:```
sudo modprobe tulip
ifconfig
```Do you now see an ethernet interface? eth0, perhaps? Can you now connect your ethernet cable and do:```
sudo dhclient eth0
```Did you connect?

---

### Post by SirScott13 on 2009-03-24
Ok, I've run all of those commands.  When I ran the ifconfig, it returned two links:
lo and wlan1, but no eth0.  My wireless card works fine, but I use it at home and work and my office doesn't have wireless.

---

### Post by chili555 on 2009-03-24
Will you please post:```
dmesg | grep tulip
lspci -nnm
```This is a PCI device, right? Or is it a PCMCIA? If it's a PCMCIA, please post:```
lspcmcia -v
```Also, while your wireless is running, please do:```
sudo update-pciids
```Next, let's look at:```
cat /usr/share/misc/pci.ids | grep ADMtek
```Hopefully, you will see something like:> 1317  ADMtek
	ab02  ADMtek Centaur-C rev 17 [D-Link DFE-680TX] CardBus Fast Ethernet Adapter
	0001  **MN-120** (ADMtek Centaur-C based)
	0002  MN-130 (ADMtek Centaur-P based)I think this indicates we are getting close!

---

### Post by SirScott13 on 2009-03-24
This looks like it is heading in the right direction.  I will have to wait until I get home to my wireless account tonight to run that command.  As soon as I do, I'll post the results.  Thanks for you help.

---

### Post by SirScott13 on 2009-03-24
Ok, just for kicks and giggles I ran that last command to see what the result was.  It is exactly as you posted.

---

### Post by chili555 on 2009-03-24
> [COLOR="Red"]1317[/COLOR] ADMtek
ab02 ADMtek Centaur-C rev 17 [D-Link DFE-680TX] CardBus Fast Ethernet Adapter
[COLOR="Red"]0001[/COLOR] MN-120 (ADMtek Centaur-C based)

I will be fascinated to see if your card identifies itself in *lspci* or *lspcmcia* as 1317:001.

Please provide the other data requested at your convenience.

---

