---
title: "HOW to: Remote adminsration of Mythbuntu box?"
date: 2009-10-09
forum: Mythbuntu
---

### Post by chipppy on 2009-10-09
Good morning

I want to setup a remote type administration of my mythbuntu box (9.10beta) from my Ubuntu (gnome desktop) box.

Both boxes are currently connected to the same ADSL 2 modem/router in separate ports.

does anyone know of where i can find a good HOW TO: (read idiots guide for me).  I dont have any networking experience so this is all new to me.

My Mythbuntu box is connected to an old CRT TV so the resolution is not good enough to do any adminstration type work and I currently have to move the box and connect it to my Ubuntu box LCD monitor.  I want to overcome this by remote adminsrating my Mythbuntu box

Any and all help is greatly appreciated

Cheers
chipppy

---

### Post by SiHa on 2009-10-09
I believe VNC and SSH servers are installed and enabled by default on Mythbuntu.

If you don't know the IP address of your Mythbox, in a terminal window, type: ```
ifconfig
```This will return a load of network information, and the IP address should be in the **eth0** section at the top - probably 192.168.1.101 or similar.

So, now you can remote login to a terminal session on the Mythbuntu box with SSH. In a terminal window type ```
ssh mythbuntuuser@myth.box.ip.address
``` substituting for the normal Myth user and the IP address you just got. You will be prompted for the password. This should be the password for that user on the Mythbox, not the Ubuntu box.

This will let you do anything that you can do from a terminal window alone. If you want to launch any GUI apps remotely, you can change it to:```
ssh -X mythbuntuuser@myth.box.ip.address
```This will export an X-server session to the Ubuntu box, so any GUI you launch from the terminal will appear on the Ubuntu box, not on the Mythbox.

The advantage of using SSH, is that it will not touch the desktop on the Mythbox, someone else could be watching TV on it and not know.


If you just want remote access to the Desktop of the Mythbox, you can use the remote desktop viewer, which I think I somewhere in the Ubuntu menus (can't remember where). If it's not installed, you can install a VNC client (I use Vinagre)```
sudo apt-get install vinagre
```When you run this, just enter the IP address, and you'll be prompted for the password again.

Myself I find VNC very laggy, so I don't use it often, I prefer to use SSH.

_**A couple of tips:**_

If you want to regularly use SSH, you might want to setup passwordless authentication, there's loads of guides out there.

You also might want to setup a static IP address for the mythbox, again there's plenty of guides. like [[COLOR="Blue"]_this_[/COLOR]. I've never tried this method, as I use 8.04 which apparently doesn't have the network manager bug](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

---

### Post by joho500 on 2009-10-10
Mythbuntu comes standard with X11VNC server. With this version of VNC you connect to the active screen of your mythbuntu box, that is with the resolution set for your TV. You can activate it in mythbuntu control centre (MCC). Normal VNC server opens a new screen when you connect. You have to install it yourself. I thinks vnc4server is shipped with Ubuntu.
I use a NX server from NoMachine ([www.nomachine.com](www.nomachine.com)). You can also use FreeNX. That's a different system that opens new screens too, but works faster than VNC.

Cheers,
Joost

---

