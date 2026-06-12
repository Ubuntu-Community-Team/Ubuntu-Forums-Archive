---
title: "Adding second NIC card to a dedicated  Mythbuntu server"
date: 2015-01-10
forum: Mythbuntu
---

### Post by hollywoodpete on 2015-01-10
I have a PowerEdge 860 server with 2 NICs. Only one of them is being used. I read an interesting thread on the mailing list which mentioned plugging an HDHomeRun Prime into a second NIC card to avoid network interference by not running through the router. It makes perfect sense for me to do this since my server has an empty NIC and my HDHomeRun is sitting on top of the server. The only thing holding me back is I am unsure of the network settings. Currenttly I have this:

auto lo eth0
iface lo inet loopback
iface eth0 inet static
    address 192.168.1.90
    netmask 255.255.255.0
    gateway 192.168.1.1

Any help would be appreciated.

---

### Post by TheFu on 2015-01-10
I haven't done it, but HDHRs default to a 169.x.x.x subnet (or is it 168?). I think there is an RFC about that, so if you put your server onto that and used a crossover cable, it should work (having a switch might be nice, should you want to add another tuner). Might need a route setup specifically for that subnet - just add it to the post-up section in your interfaces file.

Just yesterday I had to reboot everything here (cold power loss) and I didn't bring up the DHCP server so the two HDHRs here weren't dropped onto my normal LAN.  Of course, you could run a tiny DHCP server jsut for that subnet and those devices - I wouldn't bother.

---

### Post by hollywoodpete on 2015-01-12
After several days, I finally got it working. I had some help from here: [http://www.silicondust.com/forum2/viewtopic.php?t=4088](http://www.silicondust.com/forum2/viewtopic.php?t=4088)
I had to disable networkmanager, edit the /etc/network/interfaces file, "if up" and restart the network. Everything works fine and I didn't have to change the IP adresses on the backend for the input devices.

auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.90
    netmask 255.255.255.0
    gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 169.254.5.12
netmask 255.255.0.0

No switches or crossover cables required

---

