---
title: "Ubuntu wont keep Static IP on restart"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by bruceleeroy on 2009-03-28
Hey guys,
I assigned my computer a static IP and 2 DNS servers for it to use.
Everything works perfectly except when I reset the computer it reverts back to the Automatic DHCP settings but it does keep the 2 DNS servers.

I followed the instructions to add the 2 DNS servers in the resolv.conf file and that worked perfectly. Unfortunately I cant figure out how to make the IP address save.

Any help would be greatly appreciated.

---

### Post by superprash2003 on 2009-03-28
try inserting the static ips to your /etc/network/interfaces file

for reference : [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by bruceleeroy on 2009-03-28
Thanks for the link.
I followed the instructions but ran into two problem:

He says to type [COLOR="Red"]sudo gedit /etc/network/interfaces[/COLOR]
and to find this line in the document:

[COLOR="Blue"]iface eth0 inet dhcp[/COLOR]

In my document I don't have that line instead mine reads:

[COLOR="Blue"]auto lo
iface lo inet loopback[/COLOR]

So I replace the iface part anyway with my IP address, netmask, and gateway.

But I figure none of that did anything because when I type in the following instructions this is what I get:
```

chris@otacon:~$ [COLOR="Red"]sudo /etc/init.d/networking restart[/COLOR]
 * Reconfiguring network interfaces...                                          SIOCDELRT: No such process
                                                                         [ OK ]
chris@otacon:~$[COLOR="Red"] sudo ifdown eth0[/COLOR]
ifdown: interface eth0 not configured
chris@otacon:~$ [COLOR="Red"]sudo ifup eth0[/COLOR]
chris@otacon:~$ 
```

Once I restart the connection it still has its default IP address and not the static one I assigned.

---

### Post by chickpea on 2009-03-28
Hi, bruceleeroy.
It doesn't seem your "interfaces" file has lines that configure eth0(your ethernet network interface card). Mine looks like below:

[INDENT]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1[/INDENT]

Just copy & paste these lines to your "interfaces" file and change the values for "address", "netmask", and "gateway" as you like. Then sudo ifdown eth0 && sudo ifup eth0. It will work.

---

