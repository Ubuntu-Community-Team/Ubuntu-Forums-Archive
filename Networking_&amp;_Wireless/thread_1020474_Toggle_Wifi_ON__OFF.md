---
title: "Toggle Wifi ON / OFF"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by confusedmatt on 2008-12-24
Hi all,

So, almost everything is working on my new Samsung NC10 but I can't workout how to toggle the Wifi on / off.

Originally, it was turned on as default, but as I need maximum battery usage and it seems that the Fn+ F9 combo doesn't work I told the BIOS to turn it off as standard!

However, I now can't find anyway to turn it on again once logged on to Ubuntu 8.10.

Any advice?

Matt

---

### Post by albandy on 2008-12-24
do a lspci in the console
it will list some of your harware. If you wireless card appears simply type
sudo ifconfig wlan0 up 
(wlan0 is the alias of the interface, it's possible that in your computer the name will be eth1 or something like that, but usually is wlan0)

---

### Post by confusedmatt on 2008-12-24
> **albandy said:**
> do a lspci in the console
it will list some of your harware. If you wireless card appears simply type
sudo ifconfig wlan0 up 
(wlan0 is the alias of the interface, it's possible that in your computer the name will be eth1 or something like that, but usually is wlan0)

Thanks for the response.

lspci did list the card, but not the address, but I got the address using iwlist scanning - it was wlan0

But the sudo ifconfig wlan0 up doesn't have any effect.

Matt

---

### Post by Jon Bradbury on 2008-12-24
> **confusedmatt said:**
> Thanks for the response.

lspci did list the card, but not the address, but I got the address using iwlist scanning - it was wlan0

But the sudo ifconfig wlan0 up doesn't have any effect.

Matt

Hi Matt

I tried that too but it made no difference - or rather, the wifi light stayed on. In order to see if the card really is still powered up, try it again and run Powertop (you need to "sudo apt-get install powertop" in a terminal first). If you see a reduction in power usage after bringing wlan0 down, you've managed it. The LED appears to be a separate device, so it works independently of the card itself (I know, it's wierd).

I haven't tried it myself, no time.. :(

---

### Post by confusedmatt on 2008-12-25
Hi Jon,

Sorry to say that Powertop shows no change, and I'm still picking up local WiFi signals.

Interestingly, when I run iwlist power I get the confusing message:

lo        no power management information.

eth0      no power management information.

wmaster0  no power management information.

wlan0     Current mode:off

pan0      no power management information.

Matt

---

### Post by Jon Bradbury on 2009-01-05
Well, I'm "confusedjon" then... I don't know enough about the driver to assist further, but I have tried various things to no avail. It's a bit like those darned fn-keys...

---

