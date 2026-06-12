---
title: "NetworkManager &amp; Internet Emergency"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by aqscithe on 2009-04-20
While attempting to gain a static ip address using this guide here:

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html")

along with several others I lost my Internet connection. This normally isn't a problem because I would just edit my connections or fix what I changed in /etc/network/interfaces or revert back to Auto eth0. Unfortunately, the guide above also calls for the removal(not complete) of Network Manager. 

Basically I don't know how to get Network Manager working again. I tried using Synaptic but, of course, since it must get the files from the internet all attempts fail. In synaptic everything is still installed(gnome-network-manager, etc.). Since, according to the guide, it is only temporarily disabled is there a way to reenable it(Please don't say fresh install). If that is not possible, is there another way to get my internet connection back. 

If you need any specifics about what was changed in the network connections, let me know, though as I mentioned before, with it being disabled and all, I'm not sure it will be much help.

I'm at a loss, frustrated(more with the static ip than anything else), and I need to get to homework collecting dust.

Thanks in advance guys and gals!!

---

### Post by dmizer on 2009-04-20
Just install network-manager-gnome

Then you can configure your network under system > administration > network

Static IP will work just fine then.

---

### Post by aqscithe on 2009-04-21
That's the thing. Network-manager-gnome is installed but the network manager has been disabled. I am just not sure of the means to reenable it. And if it were not installed the lack of an internet connection would not allow me to get the manager.

P.S. I'm dual-booting Ubuntu and Vista. That's how I'm on the internet right now.

I'll look through other parts of the forum later today. I'm sure someone has done this before.

---

### Post by dmizer on 2009-04-21
Are you unable to configure your network by going to: system > administration > network? Is there some functionality you need from network-manager that you're not getting from network-manager-gnome?

If you need a wireless management app, try wicd instead. There are directions on how to do this here: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by aqscithe on 2009-04-21
I don't know how I was able to get Wicd to download without having access to the internet but it worked. Thanks for the help and the guide you gave dmizer!! And I even got my static ip working correctly. Truly grateful.:D

---

