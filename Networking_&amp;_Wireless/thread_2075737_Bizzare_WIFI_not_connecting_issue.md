---
title: "Bizzare WIFI not connecting issue"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by pieman711 on 2012-10-24
I've just upgraded from 12.04 to 12.10 today. I compiled the driver for my network card as usual but after a reboot it wouldn't connect to my router. The network appears in the list of available networks and there are 4/5bars of signal. 
Bizzarrly it will connect to my HTC phone as a hot spot with and without secruity enabled. Also if I reboot into an old kernal but still in 12.10 it manages to connect without any problems. 
Can't for the life of me work out where the issue is. 

lspci -v:
02:08.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R
    Subsystem: Edimax Computer Co. Device 7711
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at efee0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt3562sta, rt2800pci

The driver I've been using without problems before is 
DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217

---

### Post by pieman711 on 2012-11-09
Sorry to bump this one up but I've got no further. 
I've tried bringing the router into the same room as the PC to check its not a signal problem (shouldn't be as it connects fine with older kernals) I've even tried removing network manager and installing WICD but it still wont connect. It still connects to my phone as a mobile access point without any problems. I've tried doing it through terminal using dhclient but it rather unhelpfully doesn't give any out put. When I try and use DHclient to my phone it doesn't say anything helpful just suddenly connects. 
I've even tried no encryption and changing the ESSID to make sure there are no problems with any funny characters or spaces. Again this shouldn't have been a problem as it connects to my phone without any problem. 

Any ideas where I could find some useful logs or get some information on what exactly is failing.

---

### Post by Sayiro on 2012-11-09
Unfortunately I have a similar problem and no explanation or fixes for the error.

Maybe someone out there can figure out whats wrong because I have a similar wifi chipset as you seem to have, older though.

My terminal outputs are [here. ]("http://ubuntuforums.org/showpost.php?p=12342226")

At the moment I'm running from a 10.04 LiveUSB as all seems to work flawlessly in that version.

---

### Post by rnerwein on 2012-11-09
> **Sayiro said:**
> Unfortunately I have a similar problem and no explanation or fixes for the error.

Maybe someone out there can figure out whats wrong because I have a similar wifi chipset as you seem to have, older though.

My terminal outputs are [here. ]("http://ubuntuforums.org/showpost.php?p=12342226")

At the moment I'm running from a 10.04 LiveUSB as all seems to work flawlessly in that version.
oh thats funny because i got i think i had a similar problem today too. but i can fixed it.
the problem was:
i can see my router in available wireless networks. signal was ok. but i can't connect to
my router.
what hapened --> one of my boxes is an older sony laptop and there is only one usb slot. i connect an usb hub ( 4 slots ) to the usb of the pc and instert the wlan stick ( it's a
belkin). i tried all 4 usb slots --> nothing changed. 
then i insert the pasphrase again and heurika no problem with the connection.
why i have to do this - i don't know.
may be you have a similar problem.
bye

---

### Post by pieman711 on 2012-11-10
My WiFi card is pci not usb. So I don't think thats the issue. Thanks for your help though

---

### Post by pieman711 on 2012-11-11
I've managed to get hold of a different router and tried with that and it connects fine. The only problem is it's full of o2s custom firmware and will only connect to o2 broadband. The only difference between the two routers as far as I can tell is the problematic one had WiFi protected setup. Could there be an issue with that that has been broken with the latest kernal (I'm still able to connect if I use kernal 3.2.32)

---

### Post by ahallubuntu on 2012-11-11
Can you disable WPS (WiFi Protected Setup) on the old router?  That's usually the first thing I do on any new router I setup.  I have had Linux compatibility issues with WPS before.

Are you sure the kernel in 12.10 doesn't have a built-in module (but not working) that is loaded for your wireless card?  If so, did you blacklist it before trying to build and use the driver you downloaded?

---

### Post by pieman711 on 2012-11-13
I tried disabling WPS but it didn't make a difference. In the end I've managed to sort it using the nuclear option. Complete wipe of the installation and starting again with a fresh 12.04. Previoiusly I had been upgrading from 11.10 and must have caused some problems with a years worth of tinkering. I upgraded to 12.10 without any problems and the wifi card 'just works' no recompiling whenever I update the kernal now :)

I think from now on I'll just back up my home folder and reinstall ubuntu every release rather than upgrading through the software updater. Have a good spring clean every 6 months. 
Still I wish I knew exactly what caused that bizzare pattern of selective connecting. Guess I'll never know now.

---

### Post by mpr on 2012-12-20
Not sure if you'll see this... but what was the ultimate conclusion here? 

I installed fresh onto 12.10 a few months ago. I've been using a USB wireless but got the Edimax 7128Gn, assuming it would work after being set up.

But the drivers won't make. I got them to make in kernel 3.5.0-19, but it WON'T CONNECT TO THE NETWORK. Seems the same problem you're mentioning here. I went into kernel -18 and tried to make and now it won't make again. The error lines are:

make: *** /lib/modules/3.5.0-18-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

But I fear even if I get it working it's going to stop working. Driving me nuts.

---

### Post by pieman711 on 2012-12-30
Just stumbled on this by chance while checking some of my other threads. I never exactly found out what was going on with my network device. I would imagine I had previously messed with some settings to get it to work before it was officially supported. When the official support had come out in 12.10 I had disabled some of the needed settings. After a clean install the card worked fine, out of the box so to speak. I didn't need to make the driver.

---

