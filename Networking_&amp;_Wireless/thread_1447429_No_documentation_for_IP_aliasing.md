---
title: "No documentation for IP aliasing"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-04-05
I've been looking for documentation on the "Ubuntu way" of configuring IP alias addresses, especially in Ubuntu Server (servers being where IP alias addresses would tend to be used).  I cannot find any documentation.  It seems NetworkManager also runs on the server, and has no means to do IP alias addresses.  I shut it down because it interferes with manually configured aliases (takes them back out or sometimes worse).  But I am just wondering why all this is.  I've had to modify startup/init scripts to get the aliasing working.  That's not a problem for me since I have worked in Unix at that level for so long.  But I would think there would be some standard way for Ubuntu Server (or any other) to do this.  I just can't seem to find it.

---

### Post by iponeverything on 2010-04-05
in /etc/network/interfaces

```
# alias 1
iface eth0:1 inet static
  address 192.168.1.44
  netmask 255.255.255.0
# 
# alias 2
iface eth0:2 inet static
  address 192.168.1.45
  netmask 255.255.255.0

auto eth0:1 eth0:2
```

---

### Post by Skaperen on 2010-04-05
And how do you do this WITHOUT making all the network services get restarted every time.  I suggest actually trying it with 100 IP aliases.  It will take nearly forever for the system to come back up (not a good idea for a large web service) as it restarts each service for each IP address being configured.

And try to do IPv6 which does not use pseudo interface names with :0 and :1 and such.

---

### Post by Iowan on 2010-04-05
> **Skaperen said:**
>  It seems NetworkManager also runs on the server, and has no means to do IP alias addresses.  I shut it down because it interferes with manually configured aliases (takes them back out or sometimes worse). As far as I know, Network Manager does not come on the standard out-of-the-box server install (unless it got added on the last release or two...) The "standard" server still uses */etc/network/interfaces*.

---

### Post by Skaperen on 2010-04-06
/etc/network/interfaces was what iponeverything was referring to.  But I was certainly assuming some kind of network manager in the server, even if it isn't the same one in the Gnome Desktop (is it Gnome specific?).  What comes on the server clearly isn't geared for aliases, or else there isn't documentation that tells how to do it right for it.  Doing it as individual interfaces might look right in IPv4 since it uses interface aliases to do IP aliases.  But IPv6 will be another matter since it does IP aliasing in a straight forward manner.

Some kind of sensible network management is needed in the server which can support server scale IP aliasing.  It needs to understand networking better than what we have now.  It needs to understand things like multiple IP addresses within a subnet, and multiple subnets, on an interface.  It needs to understand things like redundant fallback (move IPs to another interface if their primary interface goes down, where indicated by policy).  It needs to understand bonding multiple interfaces into one (when the appropriate module is in).

It would be nice if it were just a accessible daemon, and then let the GUI developers build eye candy for it.  One a desktop/laptop, we need things like being able to choose to have interfaces (even wireless and VPN) brought up (logged in) by default even before a user logs in on the graphical console (because they may, instead, be accessing from remote, by SSH or VNC or whatever else).  I do see this as a question often enough (e.g. "how do I make my network come alive at boot up when I'm not at home").  We shouldn't need to have to tell someone to go learn to edit files and find what to change, when it should be a pretty button in the GUI menu that says "start at boot" and "online when no user at console" (requiring administrator rights, of course).

I might just look into writing a core underlying network manager component.  Someone else will have to do the GUI part.

---

### Post by iponeverything on 2010-04-08
Over the years I have installed and managed hundreds of Linux servers and seen many, many more and not one has ever had or needed to have a GUI installed. I don't think that Network Manager could use a "server mode" interface to allow for complex network configurations to be implemented and managed via a GUI. And it sounds like that is what you are looking for.

If you do create a core underlying network manager component for server type network configurations, I see few obstacles:

- limited audience

- complex (it would need to deduce what it thinks your trying to do and not what your telling it to do)

- And it would be a very tough sell to gain inclusion of your code into the NM code base, as its focus is the desktop.

As for not having the network available without a user being logged in on desktop machines, I would not be surprised if this is not already in the feature request queue for NM.

---

### Post by Skaperen on 2010-04-08
A network manager daemon isn't essential for a server, of course.  As long as network settings stay put the way they were set through the various commands or programs, that should be good enough in most cases.

But some servers can be changing the network configuration on the fly without any desire to reboot.  But that requires some kind of coordination by both editing the config files, and doing the commands to set this.  Doing a restart on the network start script should get it right, but not always.  The most glaring example of failure is not removing IP addresses that have been removed from the configuration.

Another kind of failure should be handled in the kernel somehow, but isn't.  That is things like interface fallback.  If one interface goes down, another interface may need the IP addresses to be configured on it (and routes changed).  I have in the past done crazy hacks to get around some of this by aliasing the "lo" interface (but this also required static ARP and other mess).

A network manager should also be smarter about notifications and daemon restarts.  In many cases that isn't needed.  In other cases it is needed and isn't done.

For IPv4 aliases, it should not be necessary to specify alias interfaces.  This works better with IPv6 because the addresses are merely added to the interface.  IPv4 uses the legacy (it's time for this to go and do IPv4 the way it's done in IPv6) interface name aliasing (e.g. "eth0:2", etc).  But a program that reads a list of IP aliases for an interface could dynamically generate the interface aliases to add and delete addresses as needed ... for the IPv4 ones.

If I do decide to pursue this project, I'll also make a new file format to describe the network configuration.  To begin with, CIDR prefix lengths will be the way to specify a subnet with an IP address.  Who would use a broadcast address other than 172.16.255.255 for the 172.16.0.0/16 subnet?  The correct broadcast address and base address should be implied.  And I don't know that there is any functionality to make them different (e.g. can it even work if someone wanted such an absurdity).  I just wouldn't support that ... if you specify 172.16.0.0/16 then 172.16.255.255 is the broadcast address and 255.255.0.0 is the netmask.

This program would be usable both to read the config file and make the kernel network stack configuration be that way, then exit, or run a daemon that will allow dynamic changes.  If you specify an alternate interface for an IP address, then you'll need the daemon mode.

---

### Post by Skaperen on 2010-04-08
I am also running into the case where routes don't get changed as the interfaces change between running and non-running status (e.g. when the cable is inserted or removed).

See: [http://ubuntuforums.org/showthread.php?t=1449903](http://ubuntuforums.org/showthread.php?t=1449903)

---

