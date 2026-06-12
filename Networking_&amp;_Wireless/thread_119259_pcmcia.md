---
title: "pcmcia"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by roquefilipe on 2006-01-19
Hi, I was trying to configure an wireless connection. In windows xp a red led lightens up to indicate power (or something else) but in ubuntu when I insert the pcmcia card nothing appens. A friend said that the problem might be with the pcmcia controller. 

here is a parcial form the "lshw" command:

[PHP]           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@02:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:1c001000-1c001fff irq:19[/PHP]

I have a toshiba satallite pro A60, and the card is a U.S Robotics 802.11g wireless turbo pc card (usr 5410).
Could someone help?
thanks
flip

---

### Post by Lambert on 2006-01-19
Post the lshw part of the card. and also run this command and post the output.

cardctl ident

---

### Post by kaamos on 2006-01-19
Almost on topic: How can pcmcia devices be recognised when the system is running? My pcmcia wlan-card works perfectly if it is in the slot when the system boots, but if I insert the card later even the power led does not lit up.

I tried using "sudo /etc/init.d/pcmcia restart" but it didn't help. Any ideas?

Thanks!

---

### Post by Lambert on 2006-01-19
open your interfaces file (/etc/network/interfaces) and you'll see a line

map eth0

add a line 

map _____

insert your interface name in the blank. This should set it up to hotplug when inserted.

---

### Post by roquefilipe on 2006-01-20
in the "lshw" command I can't find any reference to the card itself. I searched with grep for card and return this:
```
flip@portatil:~$ sudo lshw | grep card
                product: PCI1410 PC card Cardbus Controller
                configuration: driver=yenta_cardbus
```
the output from "cardctl ident" with the card inserted is:
```
flip@portatil:~$ cardctl ident
Socket 0:
  no product info available
```
I was trying the "cardctl" command and with no card inserted resuts this:
```
flip@portatil:~$ sudo cardctl status
Socket 0:
  no card
```
with the card inserted results in:
```
flip@portatil:~$ sudo cardctl status
Socket 0:
  3.3V CardBus card
  function 0: [ready]
```
So I don't even suspect what the problem might be. 
A search in google made me think that it is suposed to add a line to the /etc/pcmcia/config.opts file 
```
  include port 0x3000-0x7fff, memory 0xe8100000-0xe97fffff
```

---

### Post by roquefilipe on 2006-01-24
Hi! I managed to activate the card by playing with the cardctl command. more specifically, sudo cardctl insert

next step is to configuration, but that will have to wait, since I am away from acess points for a few days.

---

### Post by nomenklatura on 2006-03-09
has any one got any further info on how to get this to work? I'm totally at a loss here....

thank you

.... and thanks to whoever said the card works "straight out of the box" in the ububtu wiki!

---

### Post by clean97gti on 2006-03-09
[QUOTE=Lambert]open your interfaces file (/etc/network/interfaces) and you'll see a line

map eth0

add a line 

map _____

insert your interface name in the blank. This should set it up to hotplug when inserted.[/QUOTE]

Here is where I'm having trouble.
in the interfaces file, I don't even see Eth0.
Now, with my laptop (Dell Inspiron 8000), the built in ethernet is actually broken and its a lot cheap to use a pcmcia for wired network access. 
How would I know what to list under map _____

---

### Post by clean97gti on 2006-03-09
OK, I misplaced my brain for a few minutes. I found it and added map eth0 to the interfaces file.
Wired network now works.:-# 

Now to get the wireless card working.

---

### Post by clean97gti on 2006-03-11
Wireless works.

I discovered why I initially had no networking. In 5.04 setup, Ubuntu detects and installs networking components before PCMCIA. Since my laptop's built-in ethernet is physically broken, Setup didn't install anything but loopback.
I upgraded to 5.10 (and it was flawless...when can you ever say that about a Windows upgrade ;) ) and pulled the wired card and popped in the wireless.
Low and behold, the wireless card was now seen as eth0 and all I had to do was give it the network name and WEP key.

---

