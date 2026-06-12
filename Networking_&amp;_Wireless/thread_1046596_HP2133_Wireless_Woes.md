---
title: "HP2133 Wireless Woes"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by firebadger on 2009-01-21
Hi,

I've managed to install Kubuntu on my new HP 2133 which was something of a challenge in itself, but now I can't get the wireless working.

This may stem from a slight misunderstanding when reading the 2133 note on the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") as I followed the NDIS Wrapper instructions for 8.04 rather than just going ahead and installing the restricted drivers. 

I have now installed the STA driver and rolled back the NDIS wrapper changes (uninstalled it, removed additions to files and removed the wpasupplicant file altogether - although I'm not sure if I should have done this). I still can't get it working.

Wireless is enabled and I can see the network is detected but I just can't connect. I am using WEP with a key phrase.

Please help me!

Further Note: The only interfaces I see on KnetworkManager are eth0 and eth1.

---

### Post by Ayuthia on 2009-01-21
Are you using Hardy (8.04 or 8.04.1) or Intrepid (8.10)?  As for wpa_supplicant, you might want to install that back.  The Broadcom STA module has problems with WEP/WPA but there is a possiblity that if one does not work, the other one will.  

The first thing that you might want to do is see if you can turn off the encryption on your router just to see if the wireless will connect to it.  If it does, then I would try using WPA to see if you can connect.

WEP/WPA has been somewhat of a problem lately with the combination of the Broadcom card and Network Manager.  Sometimes it is the module (Broadcom STA) or Network Manager that is preventing the connection.  Sometimes switching to wicd (A replacement for Network Manager) helps.

---

### Post by firebadger on 2009-01-23
Hi, Thanks for the response,

I'm using 8.10.

---

### Post by firebadger on 2009-01-23
I gave up for now. I've got a USB wireless adaptor that I'm using for now. I might wait unti 9.04 and give it another go.

Thanks Again.

---

### Post by MarkPope on 2009-01-31
Strange.  I had quite a few problems running 8.04 with NDISWRAPPER.  I tried 8.10 (Ubuntu as opposed to Kubuntu) and the wireless worked straight from the live CD.  I subsequently installed it and have had no problems yet with the Wireless connection.  I am running WPA2 rather than WEP though.  No need to mess around with NDISWRAPPER or WPA supplicant.

So why don't youu download an 8.10 iso and try it as a live CD?  it should pick up the WLAN straight away.

Hope you get it sorted.

Cheers


Mark

---

### Post by Stelil on 2009-02-03
Just in case this helps anyone... I was having what seemed like random success connecting to wireless with my hp2133 (8.10, WEP) until I found the setting for "Hardware Drivers" and found the "Broadcom STA wireless driver" was disabled. Since ticking the OK to use this driver despite it being proprietary, everything has been working perfect. I can connect OK even after coming out of suspend if I disable then re-enable networking.  

Also I bought a USB dongle by o2 and although it failed to auto configure correctly here in the UK, when I changed the default settings to..

APN - m-bb.o2.co.uk
user - o2bb
password - password

It works perfect too.

Now just need to get the mic working in skype :o)

---

