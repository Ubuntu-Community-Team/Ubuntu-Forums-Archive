---
title: "add vpn default route"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2009-02-04
I'm on 8.10 using the vpn function on the GUI.

I can connect to my company's VPN without much problem, but I always need to add a default route : route add default dev tun0

Where can I put this to make it automatic?

I see I can add some routes using the GUI, under 'IPv4 Settings'/Routes, but the UI only has fields for 'Address', 'Netmask', 'Gateway', and 'Metric'. I'm not sure how to translate 'default dev tun0' into those fields.

Is there a file to which I can add these route commands?

I tried adding a 'junk' route - '123.234.345.456' - just so that I could search for them, but it's taking forever.

Thanks,

Max.

---

### Post by Kebabman on 2009-02-04
Not sure off the top of my head how to make this a permanent route. I will have a think about it.

One thing I did notice though is that the 'junk' route you are adding is most definately junk as 123.234.345.456 is far from being a valid IP address. If you are going to test like this remember to use valid test items.

---

### Post by Kebabman on 2009-02-04
Do you get a static IP address when you connect to your VPN on the tun0 device?

---

### Post by davidmaxwaterman on 2009-02-04
> **Kebabman said:**
> Not sure off the top of my head how to make this a permanent route. I will have a think about it.

One thing I did notice though is that the 'junk' route you are adding is most definately junk as 123.234.345.456 is far from being a valid IP address. If you are going to test like this remember to use valid test items.

Yeah, fair enough. Though I wouldn't call it 'testing' as such - since I just want to set it to something unusual so that it's easier to search for. I didn't care if it worked or not - though your point is still valid since it might not bother adding such an 'address' since it's not valid (though it did seem to 'stick' in the settings, unlike other numbers :|).

I'll try 12.23.34.45, since that's a valid address.

Max.

---

### Post by davidmaxwaterman on 2009-02-04
> **Kebabman said:**
> Do you get a static IP address when you connect to your VPN on the tun0 device?

I can't say I've noticed. Why?

Max.

---

### Post by Kebabman on 2009-02-04
> **davidmaxwaterman said:**
> I can't say I've noticed. Why?

Max.

Hmm, never mind I think I am being stupid...

Do you know what the name of the GUI is that you are using (sorry I don't use gnome but if you can tell me the name of the gui program I can probably run it and see how it works, this might help me to solve the problem)

All you probably have to do is set a default route in that GUI that uses the IP address of the router that tun0 gets an IP address from.

---

### Post by davidmaxwaterman on 2009-02-04
> **Kebabman said:**
> 
Do you know what the name of the GUI is that you are using (sorry I don't use gnome but if you can tell me the name of the gui program I can probably run it and see how it works, this might help me to solve the problem)

All you probably have to do is set a default route in that GUI that uses the IP address of the router that tun0 gets an IP address from.

Its 'About' says 'NetworkManager Applet 0.7.0' and it refers to a [web site]("http://projects.gnome.org/NetworkManager/").

I don't see any place for a default route. It does have a setting for 'Gateway', which I guess is at least related - though it's not a 'dev' as per the route command. IPv4Settings has a 'Method' which is set to 'Automatic (VPN)', but nothing about default route (though the 'manual' method does allow me to set a list of what look like routes). The 'Routes...' button brings up a window allowing me to add and delete routes, though, again, nothing to allow adding a default route to a device. I can add a '0.0.0.0' with a '0.0.0.0' Netmask, but is that the same thing as a 'Genmask' (as listed in netstat -rn)?, and there's still no way to specify a device (or perhaps 'this device' is implied?).

Thanks,

Max.

---

### Post by Kebabman on 2009-02-04
> **davidmaxwaterman said:**
> Its 'About' says 'NetworkManager Applet 0.7.0' and it refers to a [web site]("http://projects.gnome.org/NetworkManager/").

I don't see any place for a default route. It does have a setting for 'Gateway', which I guess is at least related - though it's not a 'dev' as per the route command. IPv4Settings has a 'Method' which is set to 'Automatic (VPN)', but nothing about default route (though the 'manual' method does allow me to set a list of what look like routes). The 'Routes...' button brings up a window allowing me to add and delete routes, though, again, nothing to allow adding a default route to a device. I can add a '0.0.0.0' with a '0.0.0.0' Netmask, but is that the same thing as a 'Genmask' (as listed in netstat -rn)?, and there's still no way to specify a device (or perhaps 'this device' is implied?).

Thanks,

Max.

Well the only nm-applet I can run is version 0.6.5 and it seems to be missing alot of the stuff you are talking about. You are still talking about trying to add a device for the default route though whereas you need to find out the IP address of the gateway that you are getting your IP address from via DHCP and add that as the gateway address, rather than specifying a device.

Genmask basically means the same as netmask so it would be worth trying to use the GUI to add a default route (using 0.0.0.0 as you did before) and for the gateweay put in the IP address of the router on your VPN.

---

### Post by davidmaxwaterman on 2009-02-04
> **Kebabman said:**
> Well the only nm-applet I can run is version 0.6.5 and it seems to be missing alot of the stuff you are talking about. You are still talking about trying to add a device for the default route though whereas you need to find out the IP address of the gateway that you are getting your IP address from via DHCP and add that as the gateway address, rather than specifying a device.


I want to do the same as I do manually. Adding the gateway doesn't seem to work, while adding the device does. That's from memory though, and I can't try it right now to tell for sure.

However, I am not clear on this at all; let me explain a bit more what I've found to see if you can make it clearer...

When I'm using my home wifi/NAT, I have to :

wlanIP="`netstat -rn | awk '/^0.0.0.0/ && /wlan0$/ { print $2 }'`"
route add default dev tun0
route add -net 66.111.4.0/24 gw $wlanIP
route add 66.197.193.102 gw $wlanIP

(perhaps wlanIP isn't the best name, but anyway)

Basically, I want everything by default to be routed through the vpn, except a couple of addresses (one is an IMAP server and the other is an FTP server, both of which won't work on the VPN).

Now, when I'm on the network the VPN connects to, I just want the two extra addresses to go over wifi (the wifi again is some kind of NAT), but this time I have to do :

route add -net 66.111.4.0/24 dev wlan0
route add 66.197.193.102 dev wlan0

But this is just from trial and error - ie I try 'gw' and it doesn't work, so I try 'dev' and it does; or vice versa. As I say, I'm far from understanding why one works and one doesn't.

My script just tests for a 'tun0' device to decide which to do. It all works nicely, except I have to manually run the script.

> 
Genmask basically means the same as netmask so it would be worth trying to use the GUI to add a default route (using 0.0.0.0 as you did before) and for the gateweay put in the IP address of the router on your VPN.

Hrm. This rings a big huge honking bell (yeah, I know, bells don't honk)...

As part of this exchange, I tried adding the two routes :

route add -net 66.111.4.0/24 dev wlan0
route add 66.197.193.102 dev wlan0

(default route is via eth0 in this case - ie no vpn - so I don't need to do anything for that)

I tried adding these to the wifi network's 'IPv4/Routes' with :

```

destination     netmask         gateway
66.111.4.0      255.255.255.0   0.0.0.0
66.197.193.102  255.255.255.255 0.0.0.0

```

seems to have done the trick. IE, a gateway of '0.0.0.0' seems to be the same as saying 'this device'.

So...perhaps the same thing will work with the VPN route. I wonder what it would be - perhaps :

```

destination     netmask         gateway
0.0.0.0         0.0.0.0         0.0.0.0

```

that's :

destination=0.0.0.0 == default route (as in netstat -rn)
netmask=0.0.0.0 == default route (as in netstat -rn)
gateway=0.0.0.0 == this device

somewhat cryptic :(

I'll have to give it a try though, which won't happen until this evening, I guess.

EDIT: Nope, those settings won't even stick, so it must think they're not correct :(

Thoughts?

Max.

---

### Post by davidmaxwaterman on 2009-02-04
At home now, and the 0.0.0.0, 0.0.0.0, 0.0.0.0 thing doesn't work, as predicted.

Also, it seems that adding the two 66. routes can't be done on the VPN connection because the device is set to tun0, which isn't correct. Instead, I need to add them to the wlan connection - furthermore, I need to specify the gw address else it doesn't work.

I don't know why sometimes I can just specify the device and sometimes I need to specify the gw.

Anyway, I think I have the 66. routes working.

...but I still don't know how to add the default route for the VPN; ie the equivalent of :

```
route add default dev tun0
```

Note that this also seems to work (manually) :

```
route add default gw <tun0's IP> dev tun0
```

but I can't figure out how to add that to the NetworkManager's UI (mostly since the IP is dynamic)...

Any inspiration from anyone?

Max.

---

### Post by pkkid on 2009-05-07
I am having the same issue as mentioned here.  My default route when connected to the VPN is going through the VPN connection, but I want it to go through my router.

Has anyone figured out how to set this up in the network-manager UI for VPNC?

---

### Post by davidmaxwaterman on 2009-05-08
> **pkkid said:**
> I am having the same issue as mentioned here.  My default route when connected to the VPN is going through the VPN connection, but I want it to go through my router.

Has anyone figured out how to set this up in the network-manager UI for VPNC?

Note that I (the originator of this thread) no longer see this problem. I'm not sure what fixed it, and I've been using 9.04 for a little while now - I think it was fixed before that though.

I don't see anything special in the setup to account for the change.

Sorry I can't be of any help.

---

