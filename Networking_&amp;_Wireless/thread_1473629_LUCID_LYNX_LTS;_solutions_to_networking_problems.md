---
title: "LUCID LYNX LTS; solutions to networking problems"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by eltonw on 2010-05-05
If this helps anyone:
I have been following discussions in various forums and also in the Launchpad bugs list.

[FONT="Verdana"]For those who experience any [COLOR="DarkRed"]_wireless connection problems_[/COLOR] with Ubuntu Lucid LTS (10.4), 
the following should be of help.[/FONT]

For netbook / notebook owners here's the the **RaLink drivers** which can be applied after installing LUCID LTS:
[http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")

**OR:**
Ricardo Salvetri's [COLOR="DarkSlateBlue"]***patched kernel***[/COLOR] can be installed after LTS is on your system. 
:!:[N.B. Mainly for RaLink cards, but it might also work for other products]
[http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb]("http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb")

**OR,** _pending newer updates on the installed LUCID LTS_, you can use this [COLOR="DarkGreen"]***newer kernel***[/COLOR] in the meantime
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/")

**OR,** a very helpful and _[COLOR="DarkRed"]***user-friendly guide***[/COLOR]_ to obtaining and installing drivers, _provided by_ Chris Barker
[URL="http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-
wpa.html"]http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-
wpa.html[/URL]

HTH,):P

Respectfully,

---

### Post by nrj1999 on 2010-05-05
Thanks for this. The option of updating the kernel worked perfectly for me after I had lost the ability to connect to a wireless network or use a vpn connection following an upgrade from 9.10 to 10.04.

---

### Post by nrj1999 on 2010-05-06
> **nrj1999 said:**
> Thanks for this. The option of updating the kernel worked perfectly for me after I had lost the ability to connect to a wireless network or use a vpn connection following an upgrade from 9.10 to 10.04.

Just to update that the fix of using the new kernel has now become erratic. Sometimes it connects to the wireless router and sometimes it just polls constantly and keeps prompting for the wireless key. Also the VPN connection only works once and won't reconnect again. It sometimes won't even reconnect after a reboot. These wireless problems and the VPN issue are prompting me to abandon Lucid for now and wait until these networking issues have been fixed.

---

### Post by quids on 2010-05-08
I tried the newer Kernel and it worked fine allowing my wireless network to connect for the first time since I installed Lucid.

Unfortunately it caused an error with ureadahead
init: ureadahead main process (287) terminated with status 5

Not sure which is worse, so Im back Kernel 2.6.32-22 and running a cabled network again.

---

