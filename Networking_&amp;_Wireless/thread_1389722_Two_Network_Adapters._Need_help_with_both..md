---
title: "Two Network Adapters. Need help with both."
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Starblaster1234 on 2010-01-24
Dear community,

I currently have two network adapters:

1. Dell Wireless 1450 (802.11 a/b/g) WLAN USB 2.0 Desktop Adapter
2. Xtreme N Desktop Adapter (Model Number: DWA-552)

Adapter 1 is external, Adapter 2 is internal. Honestly either one would work in my Ubuntu box, but I can't seem to find any driver for it. And if I could find a driver for it, I wouldn't know what to do.

I am 100% new to Ubuntu (and Linux in general for that matter) and would like to install one of these two adapters into my Ubuntu box (the other goes into my Windows XP box and will have no problem installing since I have the Windows drivers).

Thank you for your help!
Starblaster1234

---

### Post by chili555 on 2010-01-24
I think your DWA-522 works with the module *ath9k*. It is provided here, assuming your kernel version is 2.6.31.17. [http://packages.ubuntu.com/karmic-updates/linux-backports-modules-karmic-generic](http://packages.ubuntu.com/karmic-updates/linux-backports-modules-karmic-generic)  

Find out with a terminal command:```
uname -r
```If you have internet connectivity, you can do:```
sudo apt-get install linux-backports-modules-karmic-generic
```If not, you will have to download from the link and be sure to also get the dependencies (the red dot). Put them on a thumb drive and transfer them to your Ubuntu machine. Then install with:```
sudo dpkg -i <whatever_package_you_downloaded>
```

Post back if you get stuck.

---

### Post by Starblaster1234 on 2010-01-25
After typing

```
uname -r
```it returned

```
2.6.31-14-generic
```I do not know what this means, but I have a feeling it's not the right version of Ubuntu for your link.

Also, you mentioned dependencies? I don't really understand this.

And which architecture do I get?

Finally what goes in the parameter <whatever_package_you_download>? The path of the files on the flash drive?

Thanks for answering all my inexperienced-with-Ubuntu questions. I am 100% new to it (like...installed it yesterday, no experience, uname -r was the first thing I've typed in the terminal window)

---

### Post by chili555 on 2010-01-25
We were all beginners at one point. It's no problem explaining so that you learn and become experienced.> I have a feeling it's not the right version of Ubuntu for your link.The link for 'generic' shows a dependency: linux-backports-modules-2.6.31-17-generic. You have not yet updated your new installation because, guess what, you don't have internet connectivity needed to run updates! Your running kernel version (uname -r) is 2.6.31-14-generic, so we must instead grab linux-backports-modules-2.6.31-14-generic. Here it is: [http://packages.ubuntu.com/karmic/linux-backports-modules-2.6.31-14-generic](http://packages.ubuntu.com/karmic/linux-backports-modules-2.6.31-14-generic)

Since you are running a 32-bit kernel, be sure to download the i386 version.

This package depends on dpkg and linux-image which, I am quite sure, are already installed.> Finally what goes in the parameter <whatever_package_you_download>? The path of the files on the flash drive?
That's one way to do it, but for newbies, it's probably handier to drag and drop the two files to your home/user/ folder (Places -> Home Folder) and then when you open a terminal, you are in your home directory (abbreviated ~) by default. 

You can use an asterisk to install all these files, thus:```
sudo dpkg -i linux-*
```Most likely, everything will install perfectly, but if there are problems, you will be told. Post back and we'll help you out.

If it goes as perfectly as we hope, you can then load the driver module:```
sudo modprobe ath9k
```Now let's see if we have an interface:```
ifconfig
```If you have an interface, eth0, most likely, you should actually be connected! You will know if you have an IP address.

---

### Post by Starblaster1234 on 2010-01-25
```
sudo modprobe ath9k
```just went to the next line and did nothing

then when I typed in

```
ifconfig
```it said eth0 was my Ethernet port, not the wireless card.


EDIT: Otherwise everything went fine....it didn't yell at me about anything

---

### Post by chili555 on 2010-01-25
Please let me see:```
ifconfig
iwconfig
```Thanks.

---

### Post by Starblaster1234 on 2010-01-25
ifconfig
```

eth0 Link encap: Ethernet HWaddr ________________
       0 RX packets
       0 TX packets
       0 RX or TX bytes

lo
```iwconfig

```
lo no wireless connections

eth0 no wireless connections
```

---

### Post by chili555 on 2010-01-25
Ratz! Now, how about:```
lshw -C network
```Thanks.

---

### Post by Starblaster1234 on 2010-01-25
WARNING: you should run this program as super-user.
   *-network
description: Ethernet interface
product: Ethernet controller
vendor: Intel
logical name: eth0
....
...

---

### Post by chili555 on 2010-01-25
> **Starblaster1234 said:**
> WARNING: you should run this program as super-user.
   *-network
description: Ethernet interface
product: Ethernet controller
vendor: Intel
logical name: eth0
....
...No sign of the D-link DWA-552 at all? Is it installed properly?

---

### Post by Starblaster1234 on 2010-01-25
No sign...

If you mean physically then I think so. The indicator light isn't on on the box, however I assumed that was the usage indicator.

Is there a way I can check? And would you like to continue this on a messenger? (faster :P)

---

### Post by chili555 on 2010-01-25
Please check PMs.

---

### Post by Starblaster1234 on 2010-01-25
Tuns out one of my PCI slots were bad or didn't seat as well and it worked by replacing the Ethernet card.

I don't plan on using an Ethernet cable anytime soon anyway.

---

