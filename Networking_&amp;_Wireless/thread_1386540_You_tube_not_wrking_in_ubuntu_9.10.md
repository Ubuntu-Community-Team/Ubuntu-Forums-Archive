---
title: "You tube not wrking in ubuntu 9.10"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by ras123 on 2010-01-20
Hi,
I am using ubuntu 9.10 and firefox. I can't see you tube videos, it is very slow in access the youtube pages. But no problems when using with windows. So I installed google chrome in ubuntu but no luck. Is it a network manager problem? I am using a DSL connection and also tried with ipv6 disabled in firefox. Please help

---

### Post by ljamisonii on 2010-01-20
have you tried re-installing the flash package?

---

### Post by ras123 on 2010-01-21
Yes, reinstalled firefox and adobe flash installer using synaptic

---

### Post by stim on 2010-01-21
What is the output of ```
sudo apt-get install flashplugin-nonfree
``` in terminal?

---

### Post by ras123 on 2010-01-22
Installed
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But now also the site doesn't coming

---

### Post by ljamisonii on 2010-01-22
what version number does it give for your current flash plugin?

---

### Post by pricetech on 2010-01-22
Are you running 32 bit or 64 bit Karmic ??

---

### Post by ras123 on 2010-01-23
My System is Karmic 32 bit on AMD X2 240. System is up-to-date. It was working in early in Karmic, and the problem noticed recently, I think some problems with karmic updates. I used network manager trunk ([http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu)) due to a DSL problems with karmic repository.
flashplugin-nonfree 10.0.42.34ubuntu0.9.10.1
flashplugin-installer 10.0.42.34ubuntu0.9.10.1

---

### Post by ljamisonii on 2010-01-27
> **ras123 said:**
> My System is Karmic 32 bit on AMD X2 240. System is up-to-date. It was working in early in Karmic, and the problem noticed recently, I think some problems with karmic updates. I used network manager trunk ([http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu)) due to a DSL problems with karmic repository.
flashplugin-nonfree 10.0.42.34ubuntu0.9.10.1
flashplugin-installer 10.0.42.34ubuntu0.9.10.1

The only thing I can suggest to you is perhaps some diagnostic testing can help find what caused it. Come to think of it, you wouldn't have happened to install wine before it stopped working, did you?

---

### Post by jimshawnz on 2010-01-27
Also make sure that you haven't installed security addons like NoScript or disabled JavaScript. If you have installed NoScript you need to enable JavaScript for most sites that you want to use, including Youtube.

---

