---
title: "Wireless problems with Ubuntu + XBMC"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by JustinR on 2010-02-22
Hi,

I'm using the home theater software, XBMC as my "windows manager" instead of GNOME and I can't use wifi with XBMC - even though the wireless light lights up. The wireless works just fine in windows and gnome.

Wireless Card: Broadcom Corporation BCM4312 802.11b/g (rev 01) (Using Broadcam STA wireless driver)

I'm running Ubuntu 9.10 with all of the latest updates.

I've searched Google and the Forums and can't seem to find anything but references to WPA Supplicant, which I can't find anything on. How can I get wireless configured in XBMC? Thank you.

---

### Post by gilphilbert on 2010-05-06
Hi,

I found out that NetworkManager (this is what gnome uses for network configuration) doesn't run when gnome doesn't run.

I found the easiest way to connect wirelessly is to use wicd - it runs as a daemon, so gnome doesn't need to be running.

sudo apt-get install wicd wicd-curses
sudo apt-get remove network-manager

Then reboot the machine.

You can then use wicd-curses to configure your wireless (obviously you'll need a network connection to install wicd) at the console (CTRL+F2).

Good luck!

---

