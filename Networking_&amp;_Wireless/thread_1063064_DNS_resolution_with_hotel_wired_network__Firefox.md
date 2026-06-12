---
title: "DNS resolution with hotel wired network / Firefox"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by ugm6hr on 2009-02-07
I took my new Dell Mini 9 (standard Dell Ubuntu 8.04 LPIA / Gnome) to a hotel this weekend.  The hotel had a free wired internet which I thought I'd take advantage of.

I have attached a photo of the instructions on how to connect from the hotel information pack, but essentially, it involved plugging in computer and turning on.  "Advanced" instructions were for Windows, but essentially gave advice about ensuring all network devices were enabled and DHCP was on.

Plugged the ethernet in, and the Network Manager applet confirmed that I was connected to a wired network.

I confirmed I had an IP assigned (192.168.0.8).  I was able to ping (as well as access the login screen for) the hotel router (192.168.0.1; ZyXel ZyAir ?which model).  I was able to ping 216.239.59.147 and access this webpage from google using Firefox. 

However, I could not ping [www.google.com](www.google.com), or access any webpage using a URL (as mentioned - IP addresses I knew were OK).

I have seen this type of problem described before in these forums, and noted ipv6 discussed (tried disabling in FF [http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox) first, then using an edit of the alias file [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)).  No change.

I then changed to the OpenDNS ([https://www.opendns.com/k12/start/device/ubuntu](https://www.opendns.com/k12/start/device/ubuntu)), and even made that a permanent change as described.  Still no change.  I made sure I was able to ping the domain name server IPs given there.

I can confirm that having now returned home, my networking works just fine, both wired and wifi, with my new OpenDNS settings (and worked fine with my ISP settings before).  I have changed back to re-enable ipv6.

Now I'm uncertain what else to look into.

Doing a bit of googling revealed this:
[http://aplawrence.com/MacOSX/dns_puzzle.html](http://aplawrence.com/MacOSX/dns_puzzle.html)

This appears to suggest that all UNIX-based systems misbehave with certain routers, which does not bode well.

/etc/nsswitch.conf has also been mentioned.  This is my default:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

I have removed the [NOTFOUND=return] entry, in the hope that might make it continue searching for DNS resolution, but don't fully understand what difference this would make.  Hopefully it has fixed the issue - but I won't know until I have a problem again, or stay at the same hotel.

Unfortunately, I am no longer at the hotel to try solutions, but would like to gather opinions to save to my HD for the next time I go away, in case I encounter a similar problem.

EDIT:
Still searching and found this: [http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Advice_on_the_hostname_to_specify_when_installing_Sabayon_Linux](http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Advice_on_the_hostname_to_specify_when_installing_Sabayon_Linux)
Although Ubuntu installs with an alias of localhost, but your username as the actual hostname (I think)

EDIT 2:
ipconfig /renew in Windows: [http://compnetworking.about.com/cs/windowsnetworkin1/ht/renewipaddrwxp.htm](http://compnetworking.about.com/cs/windowsnetworkin1/ht/renewipaddrwxp.htm)
Ubuntu equivalent: [http://ubuntuforums.org/showpost.php?p=5262981&postcount=3](http://ubuntuforums.org/showpost.php?p=5262981&postcount=3)
I did try disconnecting and reconnecting from NM though... so don't think it's that.

---

