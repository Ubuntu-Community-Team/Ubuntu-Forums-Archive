---
title: "How do I tell Ubuntu to use my Wifi LAN?"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by hwfa on 2009-06-27
I would like to install Ubuntu on my new Acer 5738 laptop, which came with Windows Vista Home. I have a wireless LAN/router which Vista found immediately and I was thus able to connect to the net. I ran a live distro of Ubuntu (Intrepid Ibex) which did *not* find my LAN. I am worried that if I install Ubuntu on the machine, and it can't find my LAN then I'm in deep yoghurt because I won't be able to download drivers etc. Please advise me on how I should proceed. How do I ensure that Ubuntu finds my LAN and has the necessary software to use it?

Oh, I'm a complete newbie to Ubuntu/Linux although I have used Unix in the past - just not as a sysadmin.

---

### Post by tlois on 2009-06-27
If your wireless is not working with live cd, it probably will not work right off with install and you will have to do a little work.  Do you definitely have the very latest Ubuntu?  Are you able to hard wire it with ethernet while you get it to work?

Can you put it on just a portion of your hard drive to keep Vista as backup- I always think that is a good idea when first using Linux- you may come across things that don't work and need Windows at first until you feel confident with it.

Also try doing a search for "acer 5738 ubuntu" on google and probably you will find some info on it.

---

### Post by 3rdalbum on 2009-06-28
You really need to tell us the chipset that your wireless card uses. When using Ubuntu, go to the terminal (Applications > Accessories > Terminal) and type both of the following:

```
sudo lshw -c network
```

(that's "ell ess ach double-u", as in "list hardware")

```
lspci
```

In the output of one or more of those commands, it should tell you the vendor and model number of the wireless chipset. From there, we can tell you if it's going to be easy to install a wireless driver, or not.

---

### Post by hwfa on 2009-06-28
Thanks. The lshw command gave, for the wireless interface:
=== begin result from lshw command
*-network
  description: Wireless interface
  product: AR928X Wireless Network Adapter (PCI - Express)
  vendor: Atheros Communications Inc.
  physical id: 0
  bus info: pci@0000:04:00.0
  logical name: wmaster0
  version: 01
  serial: 00:24:2b:cc:84:d8
  width: 64 bits
  clock: 33MHz
  capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
  configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE802.11bgn
===== end result from lshw

The lspci command gave a whole bunch of stuff. I *think* the only relevant line was:
=== begin lspci output
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI - Express) (rev 01)
=== end lspci output

I hope I've given enough detail. I had to type all that because I couldn't find a way of copy/pasting it from the Ubuntu terminal into a file accessible by Windows. The live CD Ubuntu seems to be able to look at my Windows drive but not write to it. But that's another thread ;-)

---

### Post by hwfa on 2009-06-30
Please, everyone, accept my apologies for wasting your time. As I said in my original post, I was running from a live CD. A friend suggested I install Ubuntu and go from there. I did. Lo and behold, Ubuntu found my wLan immediately, just like Vista had. So I'm up and running :)

Thanks for your offers to help and, again, sorry.

I may be back ;)

---

