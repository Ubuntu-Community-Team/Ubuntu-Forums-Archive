---
title: "Wireless Card hit and miss"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by s_x_g_t on 2009-12-25
OK so I am running Windows XP and Ubuntu 8.04 as a dual boot set up. Windows XP is working great and I have no wireless card issues.

With Ubuntu, I can see my router under available networks, i can get on and surf the web with low signal (router is 10 feet away) after 10 minutes the connection is lost and I cant connect to my wireless router anymore.

Is there a driver update that can fix this?

---

### Post by coffeecat on 2009-12-25
> **s_x_g_t said:**
> Is there a driver update that can fix this?

It certainly sounds like a driver issue, but we need to know details of your particular wireless chipset. Is it a PCI card? If so, post the terminal output of:

```
lspci | grep Wireless
```If you get no output with that, try:

```
lspci | grep 802.11
```But if a wireless USB dongle, output please of:

```
lsusb
```While you're in the terminal, post the output of:

```
sudo lshw -C network
```There will be a lot of output, so you'll need to copy and paste from the terminal. Please post the output in [noparse]```

```[/noparse] tags to keep the formatting readable.

---

### Post by s_x_g_t on 2009-12-25
```
00:09.0 Network controller: AMDtek ADM8211 802.11b Wireless Interface (rev 11)
```


do you have the command for windows?  I cant get the info on via Ubuntu cause of no internet. cant paste it.

---

### Post by coffeecat on 2009-12-26
> **s_x_g_t said:**
> ```
00:09.0 Network controller: AMDtek ADM8211 802.11b Wireless Interface (rev 11)
```do you have the command for windows?  I cant get the info on via Ubuntu cause of no internet. cant paste it.

Sorry to take so long to respond - Christmas visiting duties. :wink:

I don't know of any command for Windows that would be of help. The lshw command gives us information about what's happening in the Linux environment - particularly which driver is being used - so we need to do this in Ubuntu. But there is a way round your problem.

Boot up with Ubuntu and open a terminal. Do the following command:

```
sudo lshw -C network > Desktop/lshw.txt
```That will create a text file called lshw.txt on your Desktop with the information we need. I thought this would be owned by root (because of the sudo) and you would need to change ownership, but when I tried this on my system, lshw.txt was owned by my ordinary account. So, the next step is to copy this to a USB stick or CD or whatever you can use to transfer it to Windows.

Now boot up with Windows and copy the lshw.txt file to wherever you want. If you want to copy and paste the contents into your post, open it with WordPad, not Notepad - or a word processor. Raw text file conventions are different in Unix-land and Windows-land, and Notepad doesn't display it properly. Or you could simply attach the lshw.txt file to your post as an attachment.

---

### Post by s_x_g_t on 2009-12-29
~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 11
       serial: 00:e0:98:b4:4e:e5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=adm8211 latency=32 maxlatency=128 mingnt=64 module=adm8211 multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:5c:84:7f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

---

### Post by coffeecat on 2009-12-29
This network interface is unfamiliar to me:

> **s_x_g_t said:**
> ```
00:09.0 Network controller: AMDtek ADM8211 802.11b Wireless Interface (rev 11)
```

From your 'lshw -C network' output you can see that your system is using the adm8211 driver for the wireless device. This is what you need to focus on, I should imagine.

I'd do a little searching for you but my internet has slowed to a crawl at the moment - technical fault. Waiting for the phone line problem to be fixed. So I'll just give you a couple of pointers. Try searching the forum or googling for adm8211 in Hardy/8.04. Maybe someone has an answer or maybe this is a failing of this driver. I don't know. I tried googling with this search string: "site:ubuntuforums.org ADM8211 802.11b Wireless Interface", and that gives 10 pages of hits. You might want to try that (without the quotes, of course) and sift out any threads that might be useful. I can't do any more until the fault is fixed - it takes far too long - but when I'm reliably back on line I'll check this thread out.

Good luck!

---

