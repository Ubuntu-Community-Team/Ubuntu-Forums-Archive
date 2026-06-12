---
title: "Network adapter stopped working and fails to start"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by ibompotsaris on 2011-02-19
Hello all...

I have somehow messed up my network (onboard) card in the process of configuring network settings. My best guess as to how I managed to do so is that I did not use ifdown before making changes to my "/etc/network/interfaces" file. Also I think it might be relevant to mention that the sshd was running -although with no active connections at that time- since I have the service installed on my 10.04 Ubuntu Server (x64).

So step by step what I did to end up with no network connection:

1) sudo cp /etc/network/interfaces ~/myfiles/interfaces.original
2) chmod 444 interfaces.original
3) sudo nano /etc/network/interfaces and then applied my network settings (IP, netmask, etc.). The syntax and configuration of my "interfaces" file is without flaw since it was simple, typical and was assigning my up to then DHCP assigned IP of 192.168.2.3 to static.

At about that point and although "ifconfig" showed the changes had been applied as planned the network card stopped working. I could no longer ping anyone but myself and the leds both on my network adapter and on my switch were turned off.

Since my configuration also has a Windows 7 installation I rebooted to Windows in hope of troubleshooting through device manager but I got an error code 10 which means that the adapter could not start.

Did I fry my network adapter for good and for all or I still have a chance of repairing it?

PS: After a closer look I saw that the NIC's LEDs indicate that the device cannot start. I am considering to reboot my MB as a last resort since the NIC is an onboard device and changing BIOS settings has done nothing to restore it.

---

### Post by ibompotsaris on 2011-02-20
This is just a quick reply to all that may be interested in this thread. I am not sure what caused the problem with my NIC but the fact is that I was messing with my network connections at the time. Finally after much ado I did reboot my MB and this solved the problem. 

Too bad I cannot pin down the exact cause of the failure.

---

