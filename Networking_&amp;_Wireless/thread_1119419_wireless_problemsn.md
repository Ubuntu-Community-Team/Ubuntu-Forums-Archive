---
title: "wireless problemsn"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by owy on 2009-04-07
Hi I am a brand new newbie from mac and windows and decided to become a convert.
I have installed on the entire drive on a macbook pro the new Kubuntu 2009.
I have ethernet 
While I have an wireless card it is not allowing it to be detected by tihe network for some reason. 
This is the info I got as follows:
~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

Help now what guys...??
owy

---

### Post by abn91c on 2009-04-07
in the mai menu applicATIONS>system>hardware drivers
check if the drivers are listed there for "activation" if so click on activate this driver, connect the wired cable just long enough for kubuntu to download the drivers, then disconnect cable, activate wireless driver, log out log in then setup the connection in the network namager

---

### Post by owy on 2009-04-08
I looked as instructed, but the only thing showing is my nvidea card. My wireless card is not showing.
Err now what.
owy

---

### Post by abn91c on 2009-04-08
Sorry, i read your post too fast, check the ubuntu apple forum. I have a dell laptop

---

