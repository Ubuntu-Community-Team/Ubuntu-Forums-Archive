---
title: "unable to connect to net, wired or wireless"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by tom.j on 2009-03-15
Just did my first ever linux install, ubuntu 8.1 on a dell latitude c600 with linksys wrtwpc54g v3 pcmcia wireless g card and internal 3com 3c556 ethernet > linksys wrt54g wireless router with 128 bit wep.  I am unable to connect to the internet with either the wireless card OR a wired connection.  The wireless card is detected (I can see that with hardware testing) and appears in network connections as "auto eth0" that says "never" next to it (what is that for?)but auto eth0 appears in wired rather than wireless connections. The network icon has an "!"
  I tried to add a wireless connection, calling it "linksys" the default ssid that I use, mode=infrastructure, bssid blank, mac address blank, mtu automatic, security wep 40/128 bit key using the passphrase for my network, wep index 1, authentication open system, ipv4 settings: method automatic (dhcp), and the dhcp client id blank- still wouldn't work.
   At first I thought I'd have to install windows sys and inf driver files using the ndis wrapper, but I have no connections and the ndis wrapper graphical interface does not appear in the synaptic package manager- and I can't do an update without an internet connection, but after reading a bit more I tend to think the drivers got installed correctly somehow during the ubuntu installation and its my network settings.  I'm totally lost, new to this linux thing & from windows background, any ideas?

tom

---

### Post by abyssius on 2009-03-15
> **tom.j said:**
> Just did my first ever linux install, ubuntu 8.1 on a dell latitude c600 with linksys wrtwpc54g v3 pcmcia wireless g card and internal 3com 3c556 ethernet > linksys wrt54g wireless router with 128 bit wep.  I am unable to connect to the internet with either the wireless card OR a wired connection.  The wireless card is detected (I can see that with hardware testing) and appears in network connections as "auto eth0" that says "never" next to it (what is that for?)but auto eth0 appears in wired rather than wireless connections. The network icon has an "!"
  I tried to add a wireless connection, calling it "linksys" the default ssid that I use, mode=infrastructure, bssid blank, mac address blank, mtu automatic, security wep 40/128 bit key using the passphrase for my network, wep index 1, authentication open system, ipv4 settings: method automatic (dhcp), and the dhcp client id blank- still wouldn't work.
   At first I thought I'd have to install windows sys and inf driver files using the ndis wrapper, but I have no connections and the ndis wrapper graphical interface does not appear in the synaptic package manager- and I can't do an update without an internet connection, but after reading a bit more I tend to think the drivers got installed correctly somehow during the ubuntu installation and its my network settings.  I'm totally lost, new to this linux thing & from windows background, any ideas?

tom

You don't need to connect to the Internet to install ndiswrapper. It is located on your live CD. If you browse your CD, you’ll see directory named [pool].  If you open [pool] -  this will lead you to two sub-directories: [main] and [restricted].  Open the [main] directory and you will see several directories labeled alphabetically.  If you open the [n] directory, you’ll see two directories labeled [ndiswrapper] and [ndisgtk].

The procedure is to open the [ndiswrapper] directory. You’ll find two install packages: ndiswrapper-common and ndiswrapper-utils. First, install the ndiswrapper-common package (double-click on it). Next, install ndiswrapper-utils in the same fashion. Next, go one directory level up (back to where you saw the [ndisgtk] and [ndiswrapper] directories).  Open the [ndisgtk] directory and install that package.  This adds a [Windows Wireless Drivers] menu item to your [Administration] menu. Run the Windows Wireless Drivers menu and direct it to your .inf file. You’re all set to install the Windows driver for your wireless adapter.

---

### Post by tom.j on 2009-03-15
got as far as putting in the package and the windows drivers, then some damn keyring password nonsense thing locked me out of the whole pc...

so I'm reinstalling ubuntu and starting over...

tom

---

### Post by tom.j on 2009-03-16
redid the ndisgdk thing after the reinstall and it worked, but only after I disabled security on my router.  Seems like it was unable to find the router until I disabled router security, then when it did find the router I was able to reenable 128b wep and get in.

thanks for all the help!

tom

---

### Post by abyssius on 2009-03-16
> **tom.j said:**
> redid the ndisgdk thing after the reinstall and it worked, but only after I disabled security on my router.  Seems like it was unable to find the router until I disabled router security, then when it did find the router I was able to reenable 128b wep and get in.

thanks for all the help!

tom

Congrats Tom

You did everything right and have been rewarded for it. Good job!

---

