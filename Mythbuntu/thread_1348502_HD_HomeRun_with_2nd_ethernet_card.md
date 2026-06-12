---
title: "HD HomeRun with 2nd ethernet card?"
date: 2009-12-07
forum: Mythbuntu
---

### Post by bcg30506 on 2009-12-07
I'm looking into the HD HomeRun network capture device for using with our cable's QAM channels for free local HD.  I hate putting so much bandwidth onto our network since we also use it for hosting a web site and a home office.  I only need it to talk to one box, my mythbackend server.

How feasible or difficult would it be to add a 2nd ethernet port to the box and connect it directly to the HomeRun via a crossover cable instead of going through a router?  Would this speed it up and minimize network latencies for HD streams?  What speeds can it run, ie. do I need a 1GB or 100MB card?

I'd still like to leave my mythbackend on the network with the existing card obviously, so my frontends can reach it.  Thanks!

---

### Post by Nostalos on 2009-12-07
It is not difficult. At all.   Looking at the spec's on the box (i don't own one, but been thinking about it) its 100Mbit interface so no need for Gig.

Secondly,  if you are using a switch instead of a hub you won't be using your router/home network bandwidth.  Purpose of a switch is that traffic flowing between the Homerun and the Myth box (if they are on the same network segment) they are the only ones seeing that traffic.   So you should only see performance issues if you are trying to connect from a 3rd machine.  i.e.  copying files to/from your mythbox from your desktop.  If the mythbox is busy it will get slow.  But it wouldn't drag down everything in the network.

---

### Post by sk8er3810 on 2009-12-07
I broke down and purchased an HDHomeRun yesterday from Amazon for $120(including shipping) because my pcHDTV 5500 was not tuning well(I may need to send it back :( because my HDTV has no issues with the signal ).  It should be here by the end of the week so hopefully I'll have it for the weekend to play with.  I will be looking at using it on the network(mythbox and hdhr on the same switch) versus directly connected to the Mythbox as well as ATSC over the air and QAM digital cable from Comcast.  I will let you know how everything goes.

---

### Post by uncle hammy on 2009-12-07
It can certainly be done.  One thing to bare in mind, the HDHomeRun unit only uses DHCP, so you'd have to have that set up on your backend machine.

---

### Post by ZedThou on 2009-12-07
I see you're not going to connect the HDHomeRun directly to the backend after all, but for anyone in the future who would like to do just that, there are a couple of things I've learned. The HDHomeRun doesn't require a crossover cable, any ordinary cable will do (and one is included in the package), and the HDHomeRun doesn't necessarily require a DHCP server running on the backend when hooked up directly. It will assign itself an IP address if no DHCP server is found, and then mythtv-setup can detect it. The only problem with this approach is that every time you reboot the backend, the self-assigned address for the HDHomeRun will be different, which requires rerunning mythtv-setup, deleting the tuners, adding them anew, etc. So the easiest thing is to run a very barebones dhcp3-server with something like this for the configuration (here the backend ethernet port to which the HDHR is connected might have static ip address 169.254.1.1 with netmask 255.255.0.0, replace the HDHomeRun MAC below as applicable, it's printed on the underside of the unit, and change the assigned IP address to whatever you like)

```

$ cat /etc/dhcp3/dhcpd.conf

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

default-lease-time 86400;
max-lease-time 604800;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

subnet 169.254.0.0 netmask 255.255.0.0 {
}

host hdhomerun {
  hardware ethernet 00:18:DD:01:89:EA;
  fixed-address 169.254.215.251;
}

```

---

### Post by bcg30506 on 2009-12-08
> **ZedThou said:**
> I see you're not going to connect the HDHomeRun directly to the backend after all, but for anyone in the future who would like to do just that, there are a couple of things I've learned. The HDHomeRun doesn't require a crossover cable, any ordinary cable will do (and one is included in the package), and the HDHomeRun doesn't necessarily require a DHCP server running on the backend when hooked up directly. It will assign itself an IP address if no DHCP server is found, and then mythtv-setup can detect it. The only problem with this approach is that every time you reboot the backend, the self-assigned address for the HDHomeRun will be different, which requires rerunning mythtv-setup, deleting the tuners, adding them anew, etc. So the easiest thing is to run a very barebones dhcp3-server with something like this for the configuration (here the backend ethernet port to which the HDHR is connected might have static ip address 169.254.1.1 with netmask 255.255.0.0, replace the HDHomeRun MAC below as applicable, it's printed on the underside of the unit, and change the assigned IP address to whatever you like)

```

$ cat /etc/dhcp3/dhcpd.conf

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

default-lease-time 86400;
max-lease-time 604800;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

subnet 169.254.0.0 netmask 255.255.0.0 {
}

host hdhomerun {
  hardware ethernet 00:18:DD:01:89:EA;
  fixed-address 169.254.215.251;
}

```

This is VERY helpful!  Thanks.

---

### Post by eric.woodruff on 2010-03-28
I didn't want to go to the trouble of setting up a dhcp server so I just bridged eth0 and eth1, that way the mythtv box has private bandwidth to the hdhomerun, but the hdhomerun can use the general dhcp server on my network. It also means that other machines can see the hdhomerun for diagnosibility/configuration.

apt-get install bridge-utils

/etc/network/interfaces:
auto br0
iface br0 inet static
    bridge_ports eth0 eth1
    address 10.0.0.2
    netmask 255.255.255.0
    gateway 10.0.0.3

---

