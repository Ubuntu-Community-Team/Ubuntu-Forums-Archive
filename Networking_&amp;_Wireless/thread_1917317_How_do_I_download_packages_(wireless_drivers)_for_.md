---
title: "How do I download packages (wireless drivers) for installation on an offline pc"
date: 2012-01-29
forum: Networking &amp; Wireless
---

### Post by cha0s619 on 2012-01-29
[B]Hi,

I am currently using Ubuntu 10.04 as my main OS with usb wireless adapter TP-Link TL-WN727N. I used to have a wired connection so installing the drivers for the wifi adapter was simple. I just hooked up the wired connection and did:

[/B]```

sudo apt-get update

sudo apt-get install linux-backports-modules-wireless-lucid-generic

```However, I no longer have the wired connection (only wifi now) and I just installed Backtrack 5 (based on ubuntu 10.04) on another partition. How do I download and install the drivers for the Backtrack partition which cannot go online? I've tried using packages.ubuntu.com but the packages have dependencies and it is impractical to go through each one and make sure I have all the dependencies manually, especially since some packages are missing in Backtrack that would be in a regular ubuntu installation (eg Synaptic & some dependencies of other packages) .

Please help!

---

### Post by kevdog on 2012-01-29
Im confused about a couple of things.

#1 - Why can't your wired connection work with backtrack?
#2 - What wireless drivers are you looking for?  ie what chipset is your device?

---

### Post by cha0s619 on 2012-01-29
1. It's not that the wired connection won't work with backtrack but rather, the router is in my housemates room and he is away on holiday for a few weeks so I can't connect the wired cable. It hasn't been a problem because I have been using wifi on my main Ubuntu OS.

2. The chipset is **Ralink** RT3070

---

