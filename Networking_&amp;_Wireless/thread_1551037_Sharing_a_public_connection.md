---
title: "Sharing a public connection"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by hijacktheleft on 2010-08-11
So we just moved, and our laptop can pick up a free public wifi signal in one spot in our house. I was wondering if it's possible, and if so, how, to use the laptop to receive the signal, and then have a wired connection to the router so it can then broadcast the signal, so other computers/devices can use it. 

I've been using Ubuntu and various other distros for a while now, but never for anything out of the ordinary. 

Thanks!


EDIT:

I installed Firestarter for the internet connection sharing aspect of it, but that's not working either.

[IMG]http://img690.imageshack.us/img690/614/firestarterscreenshot.jpg[/IMG]

As you can see, eth2 is obviously my wireless connection. eth0 is my ethernet port. When I try to enable the firewall, it says "Failed to start firewall.  The device eth0 is not ready. Please check your network device settings and make sure your Internet connection is active.

---

### Post by dmizer on 2010-08-11
Ubuntu comes shipped with the ability to share internet. You do not need Firestarter. In fact, you should probably uninstall it and use the default UFW instead. There is a GUI for UFW under system > administration > firewall configuration. If it's not installed, just look for gufw in synaptic.

Then, you should be able to configure connection sharing by right clicking on your network icon (in the notifications toolbar), and select "edit connections". Select the wired adaptor (eth0), and click "edit". Click on "IPv4 settings" and change the method to "Shared to other computers". Click "apply". Enjoy shared internet.

You may also have to install dnsmasq.

---

### Post by hijacktheleft on 2010-08-11
That worked perfectly. Thank you!!

---

