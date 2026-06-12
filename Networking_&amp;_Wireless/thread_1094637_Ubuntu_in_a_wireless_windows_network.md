---
title: "Ubuntu in a wireless windows network"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by RangoTheClown on 2009-03-12
Hi all,

I have a Linksys wireless G router in my home.  I have Ubuntu Intrepid installed on my desktop (along with XP in dual boot, but that's not important here).  There are two other computers in my house that I use periodically, both of which run Windows XP.  What I have found is that the Windows machines do not recognize the name of my Ubuntu machine (mwest-desktop), although they do recognize the IP (currently 192.168.1.102, but it is dynamic).  However, this is where it gets weirder.  If I try to ping one of my windows machines from Ubuntu using its name, it resolves into an IP that I have never seen.

For instance, if I ping westpc--a windows machine--this is what I get:
PING westpc (24.28.193.9) 56(84) bytes of data.
64 bytes from 24.28.193.9: icmp_seq=1 ttl=45 time=33.4 ms
64 bytes from 24.28.193.9: icmp_seq=2 ttl=45 time=35.6 ms
64 bytes from 24.28.193.9: icmp_seq=3 ttl=45 time=36.9 ms

However, the real ip of westpc is currently 192.168.1.105.  If I try to ping 192.168.1.105 from my ubuntu machine, this IP is also recognized.  I don't know where the other address is coming from.  I have to use the ip of the machine if, for instance I want to start a VNC connection with westpc from ubuntu.  Similarly, I have to know the ip of the ubuntu machine if I want to open an ssh connection via putty from one of my windows machines.  The problem here, again, is that the IP addresses are dynamic so I cannot simply edit the hosts file on each machine because the address is not always the same.  When I try to connect from one windows machine to another by name, the two machines have no problem.  This is primarily a convenience issue for me, but any help would be appreciated.

---

### Post by mudguts on 2009-03-12
In windows if you run CMD
then IPCONFIG
what is the IP that you're getting?

is it that 24.28.193.xxx IP?  it almost sounds like it's going through the router as opposed to staying inside the network.

does your windows network have a 'name' that the Ubuntu box isn't on perhaps?

---

### Post by RangoTheClown on 2009-03-12
no, when i type ipconfig on the windows machine, i get 192.168.1.105.  That ip is pingable, but when i try to ping it by its name (westpc), i get 24.28...

although it may have something to do with the network name

i have edited the samba.conf file and fixed the workgroup.  don't know what else to touch in that file.

On another note, when I click Places>>Network and nautilus opens (after a minute or two), a "Windows Network" icon shows up (and only that icon).  When I click it, I get "Unable to mount location    Failed to retrieve share list from server."  Probably related.

---

### Post by sgosnell on 2009-03-12
You can have the router reserve static IP addresses for each computer, so they get the same one every time.  It's in the settings somewhere - I haven't dealt with a Linksys in a long time, so I can't remember exactly where and how.  You can also tell each PC to request a specific IP, which should obviously be the same as the one the router is set to give it.  I only do this for my network printer, because if it gets a new IP each PC has to be reconfigured for that, which is a PITA.

---

