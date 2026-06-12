---
title: "Logitech Media Server with old RIO Receiver and NFS Exports how?"
date: 2021-01-12
forum: Multimedia Software
---

### Post by Raymond Day on 2021-01-12
I had this working years ago. But had to make my Ubuntu be a DHCP server. I don't want to do that now. My router is doing that.

But I think I all most got it working.

If I do this command:

root@rayday:/media/WD-10TB-2/USBdisk2-3TB/home/part2/mystuff/slimrio/tftpboot/192.168.86.52# ./ssdp.py
192.168.86.105 00:90:00:11:47:fc
192.168.86.105 00:90:00:11:47:fc
192.168.86.105 00:90:00:11:47:fc
192.168.86.85 00:90:00:11:2b:90

I have to press CTRL C to stop it. But the 1st 3 in a row turn the RIO on and off 3 times to test it.

I have 2 REO Receivers and the ssdp.py does get a IP from them. But I don't think it's not getting the NFS Exports to it. The REO display just stays on looking for server. It should have the OS from the NFS Exports.

At **/tftpboot** is a link to **/media/WD-10TB-2/USBdisk2-3TB/home/part2/mystuff/slimrio/tftpboot** my old one I had working years ago.

The /etc/exports file looks like this:

```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/tftpboot/192.168.86.105 *(ro,sync,subtree_check,insecure,no_root_squash)
/tftpboot/192.168.86.85 *(ro,sync,subtree_check,insecure,no_root_squash)
```

So that points to the old link I had working with it before.

Seems like all most there. I guess the RIO Receiver just don't see the NFS Exports. Not sure why it don't.

[They have the set up for this still at Wayback Machine]("https://web.archive.org/web/20110810013333/http://empeg.org.uk/slimrio/linux.html").

Hope some one can help. When I turn on the RIO Receiver now. It gets a IP right away just pops up looking for server. With the big RIO on the LCD.

-Raymond Day

---

### Post by Raymond Day on 2021-01-12
I think it has something to do with the ssdp.py it does get the REO to get a IP but I guess that is about it.

The [ssdp.py is on Wayback Machine here.]("https://web.archive.org/web/20110724210821/http://empeg.org.uk/slimrio/source/ssdp.py")

That is is the same code running that gets a IP of the REO when I turn it on. I stop it and the REI will then show it's IP info but when I start it the REO just stays at looking for music server.

[B]root@rayday:/media/WD-10TB-2/USBdisk2-3TB/home/part2/mystuff/slimrio/tftpboot/192.168.86.52# ./ssdp.py
192.168.86.105 00:90:00:11:47:fc[/B]

I think maybe have to edit the code in the ssdp.py to have it see the OS on my Ubuntu Server.

-Raymond Day

---

### Post by Raymond Day on 2021-01-12
What if I do run a DHCP server on my Ubuntu with another subnet it will not mess up the on in my router? Then how could I get the RIO receiver to talk to the server with another subnet?

-Raymond Day

---

### Post by Raymond Day on 2021-01-12
I edit the DHCP router so it can only gave IP to 192.168.86.245 not to 250.

So I installed **apt install isc-dhcp-server** on my server.

Now I have to edit the **/etc/dhcp/dhcpd.conf** So how do I do that so it only gives 192.168.86.246 to 192.168.86.250 it should work then. I don't want to mess this up else maybe my LAN will not work then. Then I can start the start the DHCP server on my Ubuntu server.

I think I have to edit this:

#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;

So it should look like this I think.

subnet 192.168.86.0 netmask 255.255.255.0 {
  range 192.168.86.246 192.168.86.250;

Right?

-Raymond Day

---

### Post by Raymond Day on 2021-01-12
I found a old file when I had my server.

Edit it and it looks like this now:

```
authoritative;
subnet 192.168.86.1 netmask 255.255.255.0 {
range 192.168.86.246 192.168.86.250;
option domain-name-servers 192.168.86.1, 192.168.86.1;
option routers 192.168.86.1;
option static-routes 192.168.86.246 192.168.86.247;
option broadcast-address 192.168.86.255;
}
host RIO {
hardware ethernet 00:90:00:11:47:fc;
fixed-address 192.168.86.246;
}
host RIO2 {
hardware ethernet 00:90:00:11:2b:90;
fixed-address 192.168.86.247;
}
```

But I did not start it. I don't know if I have the IP for the router. It's IP is 192.168.86.1 and my server is 192.168.86.109 So it this right. I did not start the DHCP yet.

-Raymond Day

---

### Post by Raymond Day on 2021-01-13
I ran this but the RIO still gets a IP from the main router. Not from my Ubuntu server. The /etc/dhcp/dhcpd.conf file now looks like this:

```
authoritative;
subnet 192.168.86.109 netmask 255.255.255.0 {
	range 192.168.86.246 192.168.86.247;
	option static-routes 192.168.86.246 192.168.86.247;
	}
host RIO {
hardware ethernet 00:90:00:11:47:fc;
fixed-address 192.168.86.246;
}
host RIO2 {
hardware ethernet 00:90:00:11:2b:90;
fixed-address 192.168.86.247;
}
```

Not sure about the subnet 192.168.86.109 should that be my main server 192.168.86.1 ?

-Raymond Day

---

### Post by Raymond Day on 2021-01-13
I took the power off of my router. Then I turn on the RIO but it does not get a IP then.

It looks like this now.

```
authoritative;
subnet 192.168.86.109 netmask 255.255.255.0 {
	range 192.168.86.10 192.168.86.20;
	option static-routes 192.168.86.10 192.168.86.11;
	}
```

Because my router starts at 192.168.86.30 so I though it search for a IP from 02 to 255 not 255 to 02. But it still don't get a IP from my DHCP Server Ubuntu server.

Don't get why the RIO did not get a IP went the main router was off.

-Raymond Day

---

