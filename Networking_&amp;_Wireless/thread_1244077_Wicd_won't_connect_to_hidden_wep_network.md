---
title: "Wicd won't connect to hidden wep network"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by skullmunky on 2009-08-19
I'm using Wicd 1.5.9 on Ubuntu Jaunty, on a Macbook pro with a Broadcom BCM4322.  Wireless everything worked right out of the box, BUT, I installed Wicd so I could use it in KDE instead of the kde-plasma-network-manager widget which doesn't work so good.

I'm trying to connect to a hidden network with WEP encryption, which worked flawlessly with NetworkManager before I installed Wicd.  

If I go to Network->Hidden Network and enter the ESSID, Wicd scans for a little bit and then says "No wireless networks found."

If I find the network "hidden" in the list, I can go into the Advanced properties, enable WEP, and enter the hex key; but connecting still fails.  Any other tricks I can do?

---

### Post by AlanB66 on 2009-08-19
Sometimes you have to hit "Connect" a few times. I don't know what changed, but Wicd has become less stable.

---

### Post by skullmunky on 2009-08-20
hm, interesting.  I've tried doing it about a dozen times, no luck :(  Is there any way to re-install NetworkManager by manually downloading the packages on another machine and transferring them on a usb drive?

---

### Post by knxville on 2009-12-09
I'm having the same troubles, I've tried both the built in network manager in ubuntu 9.10 to connect to my schools network, whichs is a hidden wep secured network, I think i've tried a hundred times by now, nothing happened, not even with Wicd, through terminal, trough the configuration file under /etc/network...

Bump..

---

### Post by bilderbuchi on 2009-12-09
> **skullmunky said:**
> hm, interesting.  I've tried doing it about a dozen times, no luck :(  Is there any way to re-install NetworkManager by manually downloading the packages on another machine and transferring them on a usb drive?
[http://packages.ubuntu.com/search?keywords=network-manager](http://packages.ubuntu.com/search?keywords=network-manager)
find the one you need for your distro and architecture, i think (i'm not a KDE user) in your case it's [http://packages.ubuntu.com/karmic/plasma-widget-network-manager](http://packages.ubuntu.com/karmic/plasma-widget-network-manager)

good plan in the future is to manually re-install the default network manager, then the package gets downloaded into the package cache and is available for reinstall if anything goes awry.

---

