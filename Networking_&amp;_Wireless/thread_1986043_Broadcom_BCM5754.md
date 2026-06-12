---
title: "Broadcom BCM5754"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by Disneylad on 2012-05-24
Hi Ubuntu Community 

I'm a new user to Ubuntu, downloaded and installed 12.04 on a previous Windows machine (newly converted you could say...).

But, as always, there must be one problem. That problem was no wireless driver for a **Broadcom Corporation NetXtreme BCM5754 Gigbit Ethernet PCI Express**. Could not connect to the internet through wireless.

Spent about a week on it, trying everything that I could find through the LAN connection, having no such luck.

Have tried ndiswrapper with all the add-ons and mounted and found the windows driver for the wireless card, read all instructions and followed, yet it yielded no results when the system told me that the driver was not working properly.

If anyone can help, it would be much appreciated,  
if you know of a linux driver for my current wireless card or a way through this problem, please give me a shout.

Thanks.

---

### Post by kc1di on 2012-05-24
> **Disneylad said:**
> Hi Ubuntu Community 

I'm a new user to Ubuntu, downloaded and installed 12.04 on a previous Windows machine (newly converted you could say...).

But, as always, there must be one problem. That problem was no wireless driver for a **Broadcom Corporation NetXtreme BCM5754 Gigbit Ethernet PCI Express**. Could not connect to the internet through wireless.

Spent about a week on it, trying everything that I could find through the LAN connection, having no such luck.

Have tried ndiswrapper with all the add-ons and mounted and found the windows driver for the wireless card, read all instructions and followed, yet it yielded no results when the system told me that the driver was not working properly.

If anyone can help, it would be much appreciated,  
if you know of a linux driver for my current wireless card or a way through this problem, please give me a shout.

Thanks.
Welcome to linux and Ubuntu in particular :)

first your looking at the wrong card the NetXtreme BCM5754 Gigbit Ethernet PCI Express is your Ethernet or hardwired port.
can you go to a terminal and type the following command and post the output you get here.
```
lspci
```
the l is lower case L not #1

your looking for the lines that say Broadcom 802.11 wireless or similar we need to know the type of wireless card your machine has. 

in the mean time try this go to system settings > Additional Drivers. It should offer you a propitiatory driver for you machine.  If it does install it and logout and back in see if wireless is work. if not we will try to help.

---

### Post by Disneylad on 2012-05-25
Hi David from somewhere in Maine, USA

Thank you for the speedy reply and the advice. I typed lspci, and this is what I got: 

00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)


Looked for what you recommended... didn't see it, only saw the BCM 5754. 
Went into systems, looked for additional drivers, none came up.

Unsure of what to do...

Thanks,

Disneylad

---

### Post by kc1di on 2012-05-25
Sorry so long in getting back to you bit according to the readout you do not have a wireless card installed in that machine. 

are you trying to use a usb one?

so this machine must only be capable of wired internet access.

---

### Post by kc1di on 2012-05-25
we can try these commands in a terminal see if you have a card that's hard block but i'm doubting it. 

```
lspci -nn | grep -e 0200 -e 0280
lsmod | grep -e b43 -e wl
rfkill list all
lsb_release -d
```
Again post the outputs here.

---

### Post by Disneylad on 2012-05-25
Hey there Dave

I just copied and pasted the code you gave me and this is what I got:

 lspci -nn | grep -e 0200 -e 0280
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
laurence@laurence-OptiPlex-745:~$ lsmod | grep -e b43 -e wl
laurence@laurence-OptiPlex-745:~$ rfkill list all
laurence@laurence-OptiPlex-745:~$ lsb_release -d^C
laurence@laurence-OptiPlex-745:~$

Didn't seem to do anything...
So I guess its not a hard block.

Forgive me, I did fail to mention that I am using a usb wireless (antenna thingy, inserted into a usb port).

Yet I don't know if my computer (Ubuntu 12.04) picks up the usb wireless.

Like I said, I run windows Visa AND had wireless connectivity, (no lan-cable needed) so the usb wireless was working just fine.

I believe it to be a driver problem (in my unprofessional opinion)... 

Any additional information that you would require? Just let me know.


Thanks for your patients and help, much appreciated! :D

---

### Post by steeldriver on 2012-05-25
> **Disneylad said:**
> 
Forgive me, I did fail to mention that I am using a usb wireless (antenna thingy, inserted into a usb port).

since Dave has not replied yet, can I suggest inserting the USB wireless adapter and trying the following command

```
lsusb
```

instead of lspci

---

### Post by kc1di on 2012-05-25
sorry I got busy at work.

do as steeldriver mentions.

---

