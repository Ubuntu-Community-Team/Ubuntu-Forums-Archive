---
title: "WLAN0 NOT FOUND issue"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2011-01-12
I had a clean install of Ubuntu 10.10 when after I installed ndiswrapper and used an x64 windows driver for the card, my kernel crashed. I removed the card, booted in windows and removed the driver. Ever since, my computer will not will not give me any output aside from "wlan0: ERROR while getting interface flags: No such device"

I removed ndiswrapper. Nothing changed. I think Ubuntu cannot recognize the driver anymore, but it recognizes the hardware. 

aurora@Aurora-Systems:~$ lsusub
No command 'lsusub' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
lsusub: command not found
aurora@Aurora-Systems:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=SeaGreen]Bus 001 Device 002: ID 148f:2770 Ralink Technology, Corp. RT2770 Wireless Adapter[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

aurora@Aurora-Systems:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:84:ed:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80352 (80.3 KB)  TX bytes:80352 (80.3 KB)

aurora@Aurora-Systems:~$ 

aurora@Aurora-Systems:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

Any ideas on how to go from here to fixing it without a clean reinstall?

---

### Post by amsterdamharu on 2011-01-12
I don't think you need the x64 driver.
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Ralink_USB_2.0_802.11g](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Ralink_USB_2.0_802.11g)

I don't see your exact model listed as being supported for ndis wrapper either:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB)

If you just remove the ndis wrapper and check system -> hardware drivers is it in there?
Maybe the usb already works and you don't need to do anything

At the moment I can't find the package driver/firmware for your card either:
[google]("http://www.google.com/custom?hl=en&client=pub-5386907765195439&cof=FORID%3A13%3BAH%3Aleft%3BS%3Ahttp%3A%2F%2Fwww.linuxmint.com%3BCX%3AGoogle%3BL%3Ahttp%3A%2F%2Fwww.linuxmint.com%2Fimg%2Fcse.png%3BLH%3A100%3BLP%3A1%3BVLC%3A%23663399%3BDIV%3A%23336699%3B&adkw=AELymgXuU4REWC5cBsNBryVOVJvPYO3XTedvFFZd5qnyPR1BtdMWRcXo3RumK5RrNebz1u_HtKzarsltek4FjWK8Gf2iLQNk4_olhcZRtKgy5KHaSDuMBcg&channel=5656732914&q=site%3Apackages.ubuntu.com+ralink&btnG=Search&cx=002683415331144861350%3Atsq8didf9x0")

I will download this package and see if your card is mentioned in there (the readme):
[http://packages.ubuntu.com/maverick/all/linux-firmware/download](http://packages.ubuntu.com/maverick/all/linux-firmware/download)

---

