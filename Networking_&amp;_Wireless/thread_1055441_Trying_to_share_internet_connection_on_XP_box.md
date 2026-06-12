---
title: "Trying to share internet connection on XP box"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by zoah305 on 2009-01-30
I'm running Xubuntu 8.10 on a Toshiba laptop with a software winmodem.  I gave up trying to get that thing to work but there is an XP box on my home network and I want to share its internet access with the laptop.  The network between the two is working correctly; I can share the printers and files, etc.

I've gone through all of the forum posts and documents I can find on this issue and tried all of the solutions.  At one point I had the sharing working but then I rebooted both machines and haven't been able to get it going since.  If anyone has any tips for how to do this I'd really appreciate it!

---

### Post by Iowan on 2009-01-30
I haven't tried ICS with a Windows box, but I *presume* the Ubuntu box would use the Windows box as it's gateway. Are you currently using DHCP or static addresses? (Not that it changes anything, but specifying a gateway via static address might be easier).

---

### Post by zoah305 on 2009-02-01
The XP machine is using static because it is always the gateway and the xubuntu is using DHCP.  I tried to set up the connection as static, specifying the gateway and netmask, etc., but I could't get this to work either.  Edit: I'm definitely not saying I did this correctly so it is probably still an option.  :-)

---

### Post by Iowan on 2009-02-03
Static addresses in Ubuntu are trickier than they used to be.  DHCP server *should* hand the xubuntu box the gateway address.

---

### Post by zoah305 on 2009-02-04
Ok I'll give it another shot; I've seen a few places that say to make changes to /etc/network/interfaces but this causes my network not to start properly on boot.  I've also seen some that say a command needs to be run in the terminal as well.  Is this correct or should I be able to do it all by just editing the network configuration in the system tray?

---

### Post by Iowan on 2009-02-04
There are a few commands that *could* be run in a terminal.  After changing a configuration, **/etc/init.d/networking restart**. Also, **route** will let you see what address is used for gateway (same information is available under Network Tools>Netstat).

---

### Post by zoah305 on 2009-02-05
Ok here's what I did:

right click - edit connection auto eth0
check connect automatically
uncheck system setting

IPv4 Settings:
method: manual
addresses:
          [LIST]
[*]address 192.168.0.2
[*]          netmask 255.255.255.0
[*]          gateway 192.168.0.1 (the XP box)
[/LIST]
DNS servers: threw in 192.168.0.1 (XP box)
routes:
          [LIST]
[*]address 192.168.0.2
[*]          netmask 255.255.255.0
[*]          gateway 192.168.0.1
[*]          metric  ????
[/LIST]


using command route provides the following:
Destination-----Gateway------Genmask--------Flags---Metric-------Ref-----Use-----Iface
192.168.0.0-----------*----------255.255.255.0-------U-------1----------0--------0------eth0
link-local-------------*----------255.255.0.0------U------1000--------0--------0------eth0
default---------XP box-----------0.0.0.0---------UG-------0----------0--------0------eth0


ran sudo etc/init.d/ network restart and was still unable to share the internet.  It seems to think about it for a long time when I start firefox but then eventually (like 2-3 minutes) says that the web page cannot be found.  I'm not sure what all this metrics and flags and stuff means but hopefully this helps!

---

### Post by zoah305 on 2009-02-12
Alright finally problem solved!  :P  Turns out it was the XP box's firewall that was stopping things.  I had it set to allow all network traffic but it still wouldn't work until I just exited it completely. 

The Xubuntu is using automatic DHCP and the XP has a static IP with the internet connection set as shared.  Works great.

---

