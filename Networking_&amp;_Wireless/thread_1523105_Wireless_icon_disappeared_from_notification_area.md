---
title: "Wireless icon disappeared from notification area"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by Mugendai42 on 2010-07-03
On 64-bit Ubuntu, the wireless icon was there during the first few runs of my new Asus U50 laptop, however after a reboot it disappeared. I didn't install any updates before that, although I did afterwards.

As well, the wireless also stopped working, although I installed compact-wireless from linuxwireless.org using the following command:

> sudo apt-get install linux-backports-modules-wireless-lucid-genericIt fixed my wireless again and it connected to my router, however the icon still didn't show up, so I decided to search further and found suggestions to use the command "nm-applet". When I tried it this showed up:

> An instance of nm-applet is already running.

** (nm-applet:8100): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.When I used killall on it and entered the command again, this showed up:

> ** (nm-applet:8118): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:8118): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:8118): DEBUG: foo_client_state_changed_cb
** (nm-applet:8118): DEBUG: foo_client_state_changed_cbAnyone know why this might be the case, and how to fix it?

---

