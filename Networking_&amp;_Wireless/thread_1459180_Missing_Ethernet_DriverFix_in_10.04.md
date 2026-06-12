---
title: "Missing Ethernet Driver/Fix in 10.04?"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by Todd in Berlin on 2010-04-21
**Missing Ethernet Driver in ACER 5635Z? Planned fix in 10.04?**             
                                                                Hi, just got an  ACER Extensa 5635Z. Came with Windows 7, so I installed Ubuntu 9.10 in  side-by-side configuration.

Windows 7 connects to Internet via external DSL modem but Ubuntu does  not.

I went through all the settings, set up the connection 'Wired' etc. 

The laptop has a PCI-E Gigabit Ethernet Controller which seems to be  missing its Atheros AR8131 driver for Linux... and I found a [download site ]("http://www.chipdrivers.com/chipset/network-adapter/atheros/ar8131/linux/")but it does not work... it seems that a few people have the same problem.

So, I am stuck. It was also suggested that since I am new to Ubu I just download the new beta version, and I wonder if this driver issue will be fixed with Ubuntu 10...

Thanks!

---

### Post by Ravernomina on 2010-04-21
Hey  :D

Please run these commands

```
uname -a
```

```
lspci
```

```
lsusb
```

Post Results Please :D

And also try it in GNOME. It just might be KDE

---

### Post by Todd in Berlin on 2010-04-21
Thanks, Raver. BUT is this a fix for 10.04 - which I have not yet installed - or 9.10? Both? And... actually I am such a newbie to Ubu - still with no internet connection - that i dont even know to run these commands you suggest. Thanks again...

---

### Post by chalex on 2010-04-21
To run a particular command, do Applications->Accessories->Terminal then type the command in there.  To see more about what a particular command does, type 'man <command>'.

Sounds like your network card is too new.

---

### Post by chili555 on 2010-04-21
When you do lspci, please make it:```
lspci [COLOR="Red"]-nn[/COLOR]
```I would also like to see:```
sudo modprobe atl1e
dmesg | grep eth
```That's a bit hard to read; it's ATL1E, not AT11E. 

Thanks.

---

### Post by Todd in Berlin on 2010-04-22
Great, thanks everyone for advice...

AND :)

When I am running Ubu 10 beta off the CD - without any command modifications of course - I get a network connection!

So it seems that this missing driver thing has been solved in New Ubu. 

- T

p.s. Am I the only one who calls it "Ubu"?

---

### Post by chili555 on 2010-04-22
> So it seems that this missing driver thing has been solved in New Ubu.May I assume that the loading of atl1e got your card going? A card not grabbing its driver correctly happens in a few different cases. I am not sure why. It is very easily fixed:```
sudo su
echo atl1e >> /etc/modules
exit
```

---

### Post by Todd in Berlin on 2010-04-22
Hi, and thanks again.

Actually, I did not load anything into Ubu 9.10... the developers fixed this, it seems. But the final proof is when I run the real Ubu 10 off the HD, not just from the CD.

Have a good rest of the day.
- T

---

