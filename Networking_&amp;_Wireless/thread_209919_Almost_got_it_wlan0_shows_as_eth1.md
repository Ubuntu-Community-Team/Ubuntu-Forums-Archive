---
title: "Almost got it wlan0 shows as eth1"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by harryhoudini66 on 2006-07-05
I found out the Linux driver was being loaded and that would cause the lockup. I blacklisted the driver and loaded the rt2500usb driver via ndiswrapper. Only problem is now the wlan0 shows as eth1. How do I change it?

---

### Post by ubunturules on 2006-07-05
Do you have your ethernet cord plugged into your computer.  If you do unplug it and restart your computer.

---

### Post by harryhoudini66 on 2006-07-05
I did and it still showed as eth1

---

### Post by tturrisi on 2006-07-06
Even though it says eth1, does it work?

---

### Post by harryhoudini66 on 2006-07-06
no

---

### Post by ubunturules on 2006-07-06
Try this:
```
sudo gedit /etc/modprobe.d/ndiswrapper
```
and change eht1 to wlan0, save an then reboot.

---

### Post by harryhoudini66 on 2006-07-06
Sorry, I forgot to mention that I had done that already.

---

### Post by stupidkid on 2006-07-06
Uh why does it matter what interface it is? So does eth1 work?

---

### Post by ubercat on 2006-07-06
Every ubuntu installation I've done -- six or so -- with 802.11 has ID'd the card as eth1. I've never seen wlan0 in an applet. But YMMV.

---

### Post by PsychicPsycho3 on 2006-07-06
I'm having this same problem, and it must matter because I can't get online with the wireless identifying itself as eth1.

I was able to get the wireless monitor to appear after I changed the wlan0 to eth1 in the ndiswrapper (the opposite of the advice given above), disabling eth0, and typing eth1 into the network monitor, but I still can't connect.

---

### Post by harryhoudini66 on 2006-07-07
stupidkid:

No it does not work. You can see that I stated this already when asked by the other guy.

Right now I gave up on it with the F5D7050 and jumped to the Pre-N Belkin. It shows up correctly as WLAN0 and allows me to enter a WPA Key. Problem is I cannot connect. Even when I remove the encryption from my router for testing purposes. I am not sure if the issue is the Belkin Pre-N router. I am running a firmware hack which makes it work as a Linksys WRT54X. Under Windows, I have a Mac that connects along with 4 other machines.

---

### Post by kewldude606 on 2006-07-07
I do not think it is the name of the network inferface that is causing these problems.

Make sure the driver isn't loaded (modprobe -l | grep <driver>), make sure ndiswrapper -l says driver present, hardware present.  Finally, type in iwconfig and make sure eth1 doesn't say No wireless extensions.  Then do sudo iwconfig eth1 ESSID <SSID>.

And disable encryption until you get it to work without encryption.

---

### Post by harryhoudini66 on 2006-07-07
Thanks. I had done that as well. It shows up as a wireless device although it says eth1. I also double checked the driver which was being loaded and all is well. I had also blacklisted the native Linux drivers.

---

### Post by goodmaj on 2006-07-07
Try changing wlan0 to eth1 in the file /etc/modprobe.d/ndiswrapper.  You will need to use sudo to edit the file.  This worked for me when I had a similar problem.

---

### Post by harryhoudini66 on 2006-07-07
I did that too and it still did not work for me.

---

### Post by harryhoudini66 on 2006-07-07
Any other takers? Has there been anyone that actualy got theirs to work?

---

### Post by harryhoudini66 on 2006-07-07
Can anyone make sense of this? I changed my protection to Mac Filtering only to see if I can connect.

Listening on LPF/wlan0/00:11:50:24:a2:34
Sending on   LPF/wlan0/00:11:50:24:a2:34
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:11:50:24:a2:34
Sending on   LPF/wlan0/00:11:50:24:a2:34
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
bogus UDP packet length: 556
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]
harryhoudini66@LINUX-UBUNTU:~$

---

### Post by joplass on 2006-07-07
My wireless card has worked with both wlan0 (using ndiswrapper)  and eth1 (using the driver that comes with Dapper).  The understanding is that wlan0 or eth1 will work as long as everyting else is done right.  Head [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") for a good how to.

---

### Post by munsell on 2006-07-08
> **harryhoudini66 said:**
> Only problem is now the wlan0 shows as eth1. How do I change it?

edit /etc/iftab

change:

eth1 mac your-wireless-card-mac-address

to

wlan0 mac your-wireless-card-mac-address


Please note that I doubt this will fix your wireless issues.  The connection should work (in theory) regardless of whether you call it eth1 or wlan0.

Good Luck! :)

---

### Post by ubunturules on 2006-07-08
I found the fix for it.
change eth1 -> wlan0 in :
/etc/modeprobe.d/ndiswrapper
/etc/network/interface
/etc/iftab

---

### Post by mpvano on 2006-07-08
Just a quick observation about iftab!

Ifrename (the daemon that uses iftab) was not installed by Dapper in any of my clean installs! Furthermore, in my two machines that were upgraded from breezy, ifrename WAS REMOVED by the upgrade.

I'm not sure this is such a bad thing, it used to cause a great deal of confusion because people were not aware of what it was doing. I'm sure it still works, but it appears to me that dapper's networking assumes it's NOT present, and if you start remapping interfaces, you could create some interesting problems.

I haven't tried all the various drivers, but I have things working just fine here no matter whether the wireless appears as eth0, eth1, or wlan0 on my various machines. This only appears to create a problem for any manual scripting I use (some of my machines control the interface exclusively with custom scripts).

Mario

---

