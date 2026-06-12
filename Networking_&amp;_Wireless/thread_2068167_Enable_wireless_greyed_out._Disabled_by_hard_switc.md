---
title: "Enable wireless greyed out. Disabled by hard switch. Details inside"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by ltlunatic on 2012-10-08
Ok so the basic issue here is this: My wireless has not once enabled through many environments.

Wubi install: Enable wireless greyed out

Live cd: greyed out

Partition alongside win7: greyed out.

I installed all software updates, checked additional drivers, installed the latest driver for RTL8111/8168B.

rfkill list shows phy0 and phy1.

Phy0 has a hardblock on. everything else is unblocked.

Now consider this also: I have both a wireless adapter inside my laptop and a wireless usb adapter outside. The internal adapter does not work, hence why I think hardblock is on even if the external slider in 'on'.

I have tried commands such as rfkill unblock all as well as sudo rfkill unblock all.

No wireless options in the BIOS.

I have tried another laptop and desktop and they get wireless from the get go.

Ubuntu on my laptop seems to see my belkin adapter as well as my internal (ralink) one. But trying to scan networks yields no results and says network is down always.

Ubuntu version: 12.04 lts

Ask me anything else you may need to help me, thanks.

---

### Post by chili555 on 2012-10-08
Please detach the USB and let's get the internal going. Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
iwconfig
```What is the brand and model of laptop?

---

### Post by ltlunatic on 2012-10-08
ok doing that now. the laptop was said to be custom made gaming laptop when i bought it. no branding of anykind on the case.

---

### Post by ltlunatic on 2012-10-08
> **chili555 said:**
> Please detach the USB and let's get the internal going. Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
iwconfig
```What is the brand and model of laptop?
Btw since i have no net on the latop am posting from my desktop. Cant copy command outputs :l

rfkill list all

phy0 wireless lan

soft blocked no
hard blocked yes (my theory for that in the post lol)

iwconfig

lo no wireless extensions

wlan 0 mode managed access point: not accociated tx power:off power management: off RTS/Fragment thr: off

eth0 no wireless extentions

---

### Post by ltlunatic on 2012-10-08
if it will help greatly i can connect with the wire connection downstairs and post from my laptop that way.

---

### Post by chili555 on 2012-10-08
> **chili555 said:**
> What is the brand and model of laptop?Please.

---

### Post by ltlunatic on 2012-10-08
um please what? Go downstairs?

Model as far as i can tell: intel chip dual core, windows 7 installed, bios is phoenix technologies by intel?

im moving downstairs in any case BRB

---

### Post by ltlunatic on 2012-10-08
ltlunatic@ltlunatic-laptop:~$ lspci -nn | grep 0280
ltlunatic@ltlunatic-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ltlunatic@ltlunatic-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

---

### Post by ltlunatic on 2012-10-08
lol any way to do this in a live way? would go quicker. waiting further instructions.

---

### Post by ltlunatic on 2012-10-08
am now downstairs

---

### Post by ltlunatic on 2012-10-08
seem to have gone away :l

---

