---
title: "Bluetooth Net Access?"
date: 2005-03-11
forum: Networking &amp; Wireless
---

### Post by saBrEwolf on 2005-03-11
Hi,

I have a motorola V80 connected to my computer using bluetooth. Is there any way I can use the phone as a modem to get access to the internet. I've tried googling, but only found details on the palm Tungsten, which I think could get me halfway there with the dund options, but I can't think how I can make a connection. (I thought maybe pon and poff, but never had to use these before and not sure what commands to pass etc.)
On a side note, I have gnome-phone-manager and Bluetooth filesharing if these may be of use.

Thankyou in advance

---

### Post by saBrEwolf on 2005-03-16
As is my way, I've found the solution after working at it for a while.
I'll post this hoping it will help someone

basically, when using gnome-phone-manager I realised that when it connected to my phone it asked for a dial-up networking gateway.
Dial-up networking is often abbreviated to dun

I typed into a terminal and found there was a daemon "dund" available.

I typed this to see what would happen

craig@Mojolin:~ $ dund --show
rfcomm0: 00:12:8A:C5:10:D9 channel 1 pppd pid 4663

Aha! I wrote a wvdial config file with modem pointing to /dev/rfcomm0.
And configured the rest of my dialup settings and voila! It works.

Maybe this will help soomeone

---

### Post by saBrEwolf on 2005-03-16
As is my way, I've found the solution after working at it for a while.
I'll post this hoping it will help someone

basically, when using gnome-phone-manager I realised that when it connected to my phone it asked for a dial-up networking gateway.
Dial-up networking is often abbreviated to dun

I typed into a terminal and found there was a daemon "dund" available.

I typed this to see what would happen

craig@Mojolin:~ $ dund --show
rfcomm0: <bluetooth code> channel 1 pppd pid 4663

Aha! I wrote a wvdial config file with modem pointing to /dev/rfcomm0.
And configured the rest of my dialup settings and voila! It works.

Maybe this will help soomeone

---

