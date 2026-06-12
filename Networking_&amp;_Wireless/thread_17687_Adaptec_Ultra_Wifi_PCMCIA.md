---
title: "Adaptec Ultra Wifi PCMCIA"
date: 2005-03-02
forum: Networking &amp; Wireless
---

### Post by Skid on 2005-03-02
HI,

I've followed the wifi tutorial on the site, using ndiswrapper, but I can't get my card (as per topic, Adaptec Ultra PCMCIA WIFI) working for some reason.. The card is powered up, as the lights are on, but it's just not being recognised by ubuntu..

I'm running Warty, and have universe enabled, kernel 2.6.8.1-3-686.

> 
root@ion:/home/cm # ndiswrapper -i /cdrom/ADPCNDS.INF
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

Installing adpcnds
root@ion:/home/cm #


Seems to be okay..

> 
root@ion:/home/cm # modprobe ndiswrapper
root@ion:/home/cm #

..
> root@ion:/home/cm # lsmod |grep ndiswrapper
ndiswrapper            98096  0
usbcore               115684  5 ndiswrapper,usbhid,uhci_hcd
root@ion:/home/cm #


........... and finally the error:

> root@ion:/home/cm # ndiswrapper -l
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

Installed ndis drivers:
adpcnds hardware NOT present
root@ion:/home/cm #


I've used the INF from the CD that came with the adaptec ultra wireless pcmcia card

I've noticed some hotplug errors, on bootup but for some reason nothing is showing up in dmesg regarding any failures / errors related to hotplug..

Anyone able to offer me any assistance?

Thanks in advance

Skid

---

### Post by Skid on 2005-03-02
Oh, if it helps, I think the chipset is a Prism 2.5 chipset..

---

### Post by Staesys on 2005-04-27
You might want to install the wlan_ng drivers through synaptic. It worked for me. My built in wireless card is based on the same chipset and I had really flaky connections before installing this driver.

---

