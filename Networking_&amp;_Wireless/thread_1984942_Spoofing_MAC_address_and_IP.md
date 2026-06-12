---
title: "Spoofing MAC address and IP"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by Kaero on 2012-05-22
I'm still pretty new to Ubuntu, and I've been trying to spoof my MAC address and get the IP address of my laptop within a certain range but it hasn't been working the way I need it to. This is what I've been trying to do: [http://www.mythtv.org/wiki/Sasktel_IPTV](http://www.mythtv.org/wiki/Sasktel_IPTV)

I'm trying to trick my laptop into thinking that it's my cable box so I can pull channel information to use with my HTPC when it arrives, but due to my inexperience with linux I can't figure this out properly. I've replaced the contents of the *interfaces* and *dhclient.conf* files with what it says in the guide but it didn't work properly, and I'm not sure what I may have filled in wrong.

My desired outcome is for eth0 to have the MAC address that I indicate, and a 10.110.x.x IP range.

This is what I have filled in, for the sake of my explanation I'll just say my desired MAC address is 00:11:22:33:44:55. My changes are in bold.

[B]Interfaces
[/B][SIZE=1]I don't have eth1 so I'm using eth0 and wlan0, which I hope isn't what caused the problems[/SIZE]
```
# /etc/network/interfaces -- configuration file for ifup(8), ifdown(8)

# The loopback interface
# automatically added when upgrading
auto lo **wlan0 eth0**
iface lo inet loopback

iface **wlan0** inet dhcp

iface **eth0** inet dhcp
        # Set up the hardware (MAC) address
        hwaddress ether **00:11:22:33:44:55**

        # Ensure IGMP is v2 and rp_filter is OFF
        pre-up echo 2 >/proc/sys/net/ipv4/conf/**eth0**/force_igmp_version
        pre-up echo 0 >/proc/sys/net/ipv4/conf/**eth0**/rp_filter

        # Ensure multicast requests are routed to this interface
        up route add -net 224.0.0.0/4 **eth0**

```**DHClient**
```

interface "**eth0**" {
   # Note, no "routers" in this request. The default gateway for the IPTV 
   # connection won't route internet traffic. So if we don't ask for one,
   # we don't lose our 'net access
   request subnet-mask, broadcast-address, time-offset, domain-name, host-name;

   # The DNS server given to us is wrong, and will not look up any sites.
   # override this with one we know is good (In this case, the gateway address
   # for wlan0.
   supersede domain-name-servers 192.168.1.254;

   # Hello Mr. DSLAM, I am a VIP1200 box
   send host-name "CED**001122334455**";
   # See my shiny Motorola-assigned hostname?
   send dhcp-client-identifier **00:11:22:33:44:55**;
   # See my pretty Motorola-assigned MAC address?
   send vendor-class-identifier "MotoVIP1200P_sasktel-6.2.0.011";
   # And see my sasktel firmware provided ID string?
   # Please can I have a 10.110 range IP address?
   # I'm really not faking this!
}

```Now, when I check ifconfig in a terminal it shows eth0 with the MAC address I want, but not the IP. The main problem I'm having is that in the network dropdown menu eth0 and wlan0 are showing as 'device not managed'.

There are also a second eth0 and wlan0 appearing in ifconfig, except they are labelled as 'eth0:avahi' and 'wlan0:avahi'.

If anyone can assist me I'd be very grateful!

Thanks,
Kaero

---

### Post by Kaero on 2012-05-23
Anyone? :)

---

