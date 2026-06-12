---
title: "Network IP addresses... Printer conflict ????"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by MJSOnline on 2006-01-20
Hi all.

Right I am having problems with my network.

I have a DratTek Vigor2900G router running at DHCP.
Router address 192.168.1.1

I have a HP JetDirect network box at 192.168.1.10
Ok?
But every so often with I turn on the pc, the pc takes the address of the printer, 192.168.1.10

Questions...
Why?
How do I change it so it does not happen again?

Also, when my g/f works at home she plugs her laptop into the network and prints out.  Would changing this make problems for her too?  She is using Windows XP Pro as it is a works laptop.

Thanks in advance.
Matthew

---

### Post by Lambert on 2006-01-20
The questions would be

HOw is your printer assigned an ip? I would guess static.

Your pc is being assigned an ip via dhcp.

So to solve your problem, if above is correct, you have 2 options.

1. Go into your router settings and change the ip assignment range as of now it's range includes .1.10. You need to make sure the range is outside of any static ip settings you're using. Otherwise dhcp just rotates and grabs ips with in the range setting.
2. Change the static ip on the printer so it's outisde of the range of your dhcp router/server settings.

---

