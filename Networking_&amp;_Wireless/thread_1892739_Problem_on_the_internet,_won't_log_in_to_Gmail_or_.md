---
title: "Problem on the internet, won't log in to Gmail or Facebook"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by Mountainmandoug on 2011-12-08
I just installed 11.10 on a 5-year old Toshiba Sattelite laptop that I was given. This machine was very slow with windows and prone to lock up and crash periodically. It's running much better with Ubuntu but it is very slow on the internet. I'm connected via wireless to pretty fast connection but most pages load very slowly and it refuses to log in to either gmail or facebook. I have both firefox and chromium, and firefox works a little better, but both are very slow, won't access some websites. 

I'm a low-ability lynux user and i could be overlooking something very simple, thanks for your help.

---

### Post by Scott Baker on 2011-12-08
If possible, could you please provide a little more info on your machine. Specifically, your hard drive size (and speed if you have that info available) and the amount of RAM that you're packing. The version of Ubuntu that you're running is OK with a minimum of 512mb, (1 gig or more is actually better) but combine the current version of your operating system with current versions of Firefox and Chrome, and you are likely overtaxing your machines capabilities. :-k

---

### Post by cankara46 on 2011-12-20
I have the same problem with Ubuntu 10.10 which I am using on a desktop PC having 500 GB hard disk of which not even half is used. I have 1 GB RAM. I try both Firefox and Chrome too, both give very slow speed and both  do not even open gmail sign in page.   I have dual boot with Windows XP  which works much faster. I am connected to Internet with ethernet. My Ubuntu used to be fast in the past but after doing the updates suggested by Update Manager gradually it slowed down. I have not installed any program that does not exist in Ubuntu Software Center. I want to stick to Ubuntu but this slow Internet speed forces me to switch back to Windows. I can not blame my modem or ISP since the moment I switch to Windows on my dual boot system without switching off  the modem, Internet works fine. I am 66 years old, not a PC wizard and a late starter on Linux. Any help would be much appreciated.

---

### Post by cankara46 on 2011-12-27
After lspending hours I have found out the cause of the problem! The Problem is the Network Manager.  I made my ipv4 settings manual, then everything began to work normal. To make this change in your Network Connections please see this link:

[http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/).

I hope it helps you too as it did to me.

---

### Post by Scott Baker on 2012-01-17
See, with a little research, answers do exist, and you can get those minor hiccups sorted. ):P

---

