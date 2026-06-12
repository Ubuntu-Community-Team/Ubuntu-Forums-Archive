---
title: "Only DHCP network on Kubuntu 5.10"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by runlevel0 on 2005-12-15
I recently changed from Ubuntu to Kububtu (5.10 both).

I have a home network with 3 boxes and a router.
I have always set up the interfaces statically, as this causes less problems in a small network. There are also a series of manually setup NATPT ports fitting my original settings (router 192.168.1.1 and this box 192.168.1.2

But now I have a weird problem: 

If I configure my network manually, even from a root console [1] setting up the interfaces manually, I can connect to the rest of my boxes, but... I get 'network unreachable' errors when trying to access the internet.

I can't find any dhcp-client deamon and I have no DHCP server installed (the router does).

If I use the Kcontrol>Network Settings interface (either sudo or root), I do set the proper DNS entries, but it seems that they are not written to /etc/resolve.conf.  

BTW: My network was running perfectly with my static settings on Ubunutu 5.10...

Neither I can find a dhcp-client daemon to kill, and I'm afraid that if I get rid of any DHCP software I will find myself browsing the web through my laptop or my wife's box :P

My questions: 

[list=1]
[*] How can I safely get rid of all this annoying DHCP stuff? 
[*] Shall I use attr to avoid DHCP from doing what it want's with my resolve.conf?

TIA.


My questiona are: 

I found out, that my /etc/resolve.conf only points to my router, despite having set 


[1] Yes a did create a root account.

---

### Post by FLeiXiuS on 2005-12-15
When you manually assign an interface with an IP address, do you also set the DEFAULT ROUTE?

That will be a requirement.  

Please print me the output of `route -n`

---

### Post by runlevel0 on 2005-12-15
OK; ready. I rewrote /etc/networking/interfaces from scratch, adding the default gateway and the rest of the stuff there. 
I wonder why KDE's setup tool doesn't did the job well, so I think It's time for paying a visit to the ubuntu bugzilla ;)

Ah, the workaround:

Just edit /etc/network/interfaces and do this:

* comment out any entry whcih references to dhcp, such as 
[i]
iface eth0 dhcp
[/i]

change this to 'static', add the IP address you want and the default gateway. It should look like this:
```

iface eth0 static
  address 192.168.1.2
  netmask 255.255.255.0
  gateway 192.168.1.1

```

As I explained above, my router seems to have reached a private agreement with my computer to set the network via DHCP and FUBAR all my settings, so to avoid the pesky DHCP to tamper with my settings I simply chmodded both, /etc/network/interfaces and /etc/resolve.con, despite I'm quite sure that I will get complaints from some program.
And last but not least get rid of all the DHCP stuff!

That's all. Setting up a network in Linux using the console (or an editor) is even faster as clicking your way through a "user-friendly" Wizard. 


NOTE: I am a veteran Debian user (1995).

---

### Post by ntlnsideidiotoutside on 2005-12-15
I think i have the same problem with kubuntu, route is blank.it worked fine under ubuntu.
how can i set this up for wlan0 to work with dhcp.plz help

---

### Post by runlevel0 on 2005-12-15
[QUOTE=FLeiXiuS]When you manually assign an interface with an IP address, do you also set the DEFAULT ROUTE?

That will be a requirement.  

Please print me the output of `route -n`[/QUOTE]

It seems the problem lays in rewriting /etc/network/interfaces, it didn't rewrite anything (?) and setting the default route manually didn't help either (neither *route add default eth0*, nor *route add -net 192.168.1.1*.

Rewriting of resolv.conf should not be a problem, as normally the routers have an own DNS-caching server (at least mine).

I'm now in a hurry, but I will remake the original settings so that I can check where the error is. Mi route is now right:
```

runlevel0@soviet:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by runlevel0 on 2005-12-15
[QUOTE=ntlnsideidiotoutside]I think i have the same problem with kubuntu, route is blank.it worked fine under ubuntu.
how can i set this up for wlan0 to work with dhcp.plz help[/QUOTE]

wlan0 ? that's a WiFi device.

Perhaps the necessary module is not installed (ndiswrapper or the one you use),

You could aslo try editing your /etc/network/interfaces and adding the gateway IP manually: 

```

iface wlan0 dhcp
gateway 192.168.x.y

```

remember to restart your network:

```

sudo /etc/init.d/network restart

```

I'm not sure this is necessary with DHCP, as I got everything right with DCHP (just a random IP and no NATPT). 
Are you sure you need DHCP? What about a static setting?

---

### Post by ntlnsideidiotoutside on 2005-12-15
i'll try that *runlevel0* and post the results. thanx

---

### Post by ntlnsideidiotoutside on 2005-12-15
ok heres my /etc/network/interfaces 

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#script grep
#map eth0
^^^^^
i dont use the ethernet port this is a laptop



iface wlan0 inet dhcp
gateway 192.168.2.1 (router ip)
netmask 255.255.255.0
wireless-mode managed
wireless-essid belkin1
wireless-key XXXXXXXXXX
auto wlan0

wlan0 is on after boot and the kwifi manager scanner picks up belkin1

[COLOR="Red"]route-n[/COLOR] is still blank
any ideas

---

### Post by runlevel0 on 2005-12-15
The only thing I can think on is checking if the proper modules are loaded (this depends on your hardware). There is also a very silly possibility: That your assigned IP address is 192.168.**1**.x this would be incompatible with the IP of 192.168.**2**.x, with this netmask both addresses must match the first 3 numbers. Perhaps the routers DHCP server (or your client) is assigning an address in the wrong range. I know it's silly, but it happens sometimes...

---

