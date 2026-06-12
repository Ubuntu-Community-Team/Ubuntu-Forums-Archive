---
title: "Netwokr Manager Damaged"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by Nsider on 2009-05-12
Hi there everybody
I was installing the available desktop environments in ubuntu 9.04 in order to check what best fitted my needs.
Therfore I had installed ubuntu and donwloaded the kde-desktop, eveything so far so good.
Then I, after doing some research, found enlightenment and installed it (E17 version).
THis resulted in a damaged network manager applet module (the little icon where you select the wireless network next to the clock). So therefore its very hard for me to connect to the internet.
The conenction itself its intact because it is still recognizing my hardware and therefore donwloaded the wifi-radar or something like that in order for me to connect wirelessly. It works but im only able to connect to unprotected networks. 
THerefore What I am asking is that if there is a way of either:
1) Repair that module in order to connect to wireless from gnome, kde, and enlightenment
2) Show me the correct way to connect using wifi-radar (i think) to a WEP protected network, because It always says not connected

Thanls for reading!

---

### Post by Peter09 on 2009-05-12
Have you tried re-installing network-manager?

---

### Post by Nsider on 2009-05-13
not really since I dont know the name of the module itself.
Anyway here is a screenshot of what happened along with the network interfaces.

I managed to get running the ethernet again (somehow it was not up)
and turned down all of the avahi modules. but now, the network selector (again the next to the clock icon where you pick your wifi) its gone, and when I put in the network manager from the add to panel menu, its a different one.
Please help



EDIT----- MANAGED TO CONNECT WIFI AGAIN BY RUNNING:
sudo ifconfig eth1 auto

but still no network selector working properly

please help

---

### Post by Peter09 on 2009-05-13
Try System->Preferences->Startup Applications

Scroll through looking for network-manager - make sure the box is ticked so that it will start up automatically.

if this does not work try

```
sudo apt-get install network-manager
```

---

### Post by shadowlemon on 2009-05-13
Can you connect to WIFI with WPA/WEP in GUI?
im also experiencing some trouble, as installing WICD damaged
and removed my original Knetworkmanager and nm-applet in jaunty.

---

### Post by Oblivion.Wielder on 2009-05-13
Managed to solve it:
Here is a summary of what happened:
After installing enlithenment (17 E) somehow the next things happened
-The Ethernet (eth0) module went down
-the wifi module (eth1) was completely broken
-a lot of avahi modules(what the hell are these for) were installed in place, this caused the network manager (now called network-manager-gnome in jaunty) to brake/uninstall

Therefore to successfully repair the network and get back the network selector icon this is what I did
-bring the ethernet module up (sudo ifconfig eth0 up)
-bring down every avahi related module (sudo ifconfig <avahi module name here> down
-reconfigure the  wifi module (sudo ifconfig eth1 auto)
-install the network manager icon (sudo apt-get install network-manager-gnome)


Thanks everyone for their help (especially peter for the network manager advice)

Things to notice

Yeah Im Nsider, this is my other account that I had forgotten the password for XD
The network manager module changed with jaunty/ added the gnome part to it
havent tried how this repaired kde and enlightenment
wifi-radar didn't let me connect to a WEP protected network (my home network)

THis can now be closed ^-^

---

### Post by shadowlemon on 2009-05-13
thanks for adding how you solved this, might be of great help for me

---

### Post by Oblivion.Wielder on 2009-05-13
my pleasue!

Ahh! I love when things go right!:KS:popcorn::KS

---

