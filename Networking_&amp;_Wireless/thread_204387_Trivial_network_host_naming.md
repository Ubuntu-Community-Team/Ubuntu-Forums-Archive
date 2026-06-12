---
title: "Trivial network host naming"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by dyssident on 2006-06-26
In really drawing a blank here: can anyone think of a simple way of dicovering hostnames/ips of machines on your local subnet? The Windows analog would be CIFS' network name broadcasting that allows network browsing.

None of the Linux file sharing services (NFS, SFTP) seem to have a naming component. It seems like everyone is expected to maintain multiple hosts files or memorize ip addresses.

---

### Post by banadushi on 2006-06-27
This is why DNS was invented.

If you are using DHCP, then you can configure it to update the DNS information everytime it gets a new IP.

Now if your talking about discovering shares, that's another thing, the 'Network Servers' link in places should discover stuff on the local subnet reasonably well.  But this relies upon samba and SMB.

Avahi and zeroconf may help in the future, but unless you really want to configure a bunch of stuff, they don't do much right now.

Happy Hacking!

Jason

---

### Post by dyssident on 2006-06-27
[QUOTE=banadushi]
This is why DNS was invented.
[/QUOTE]

Im looking for something more than just simple host naming like DNS does. What Im really after is a simple way of seeing whats 'out there' on ones subnet ala CIFS.

[QUOTE=banadushi]
If you are using DHCP, then you can configure it to update the DNS information everytime it gets a new IP.
[/QUOTE]

Sorry, I should have been more clear: Im specifically interested in this for home users. I would venture to guess that on most multi-box home networks, DHCP is being used, but not DNS.

[QUOTE=banadushi]
Now if your talking about discovering shares, that's another thing, the 'Network Servers' link in places should discover stuff on the local subnet reasonably well.  But this relies upon samba and SMB.
[/QUOTE]

Im mainly trying to discover machines and their hostnames, but shares would be gravy. Im specifically trying to avoid samba while still getting similar functionality.

[QUOTE=banadushi]
Avahi and zeroconf may help in the future, but unless you really want to configure a bunch of stuff, they don't do much right now.
[/QUOTE]

Oh how sweet it will be when that fine day finally arives.

I think my next step is to read up on NIS; I know next to nothing about it, but it seems like host discovery _may_ be in its wheelhouse.

---

### Post by bforbes on 2006-06-28
If you have a box that is on all the time, install a DHCP server on it, and a DNS server. That is a perfect solution.

---

### Post by dyssident on 2006-06-28
[QUOTE=bforbes]If you have a box that is on all the time, install a DHCP server on it, and a DNS server. That is a perfect solution.[/QUOTE]

Now that I think about it, I probably should have given this thread a better name. Im not concerned with naming or giving ip addresses to the boxes. Im looking for a simple way to discover all of the boxes on the local network in the manner of CIFS. Thanks tho.

---

### Post by soapyfish on 2006-06-28
Maybe I am missing the point of this thread but could you not use a network scanner like nmap nmapfe (use with care) it will display the IP's (and all open ports etc )of all network devices on the Lan but please be careful with this kind of tool as it can play havoc with a live network :-)

---

