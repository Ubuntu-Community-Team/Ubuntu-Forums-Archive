---
title: "A question about network addressing notation"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by sefs on 2010-03-16
Hi,

I have two subnets...

192.168.1.0/24
192.168.10.0/24

I want hosts from these two subnets to access 
a specific webserver on the 192.168.10.0/24 subnet.

I have ufw running on this webserver

instead of setting up two entries in ufw like so

```

80/tcp       ALLOW       192.168.1.0/24
80/tcp       ALLOW       192.168.10.0/24

```

I want to just have one entry by adjusting the /xx part i think?

What would be the xxx.xxx.x.x/xx to use to get that one entry.

Thanks.

---

### Post by capscrew on 2010-03-16
> **sefs said:**
> Hi,

I have two subnets...

192.168.1.0/24
192.168.10.0/24

I want hosts from these two machines to access 
a specific webserver on the 192.168.10.0/24 subnet.

I have ufw running on this webserver

instead of setting up two entries in ufw like so

```

80/tcp       ALLOW       192.168.1.0/24
80/tcp       ALLOW       192.168.10.0/24

```

I want to just have one entry by adjusting the /xx part i think?

What would be the xxx.xxx.x.x/xx to use to get that one entry.

Thanks.

The /nn notation is for specific ranges of IP addresses.

The /24 that you have noted refers to the first 24 bits in the IP address (e.g the 192.68.1 or the 192.168.10 parts).  There is no way to use the /nn notation to refer to a specific host's IP address.

---

### Post by sefs on 2010-03-16
> **capscrew said:**
> The /nn notation is for specific ranges of IP addresses.

The /24 that you have noted refers to the first 24 bits in the IP address (e.g the 192.68.1 or the 192.168.10 parts).  There is no way to use the /nn notation to refer to a specific host's IP address.

I made a mistake i should have said subnets instead of host.  I've corrected the initial post.

---

### Post by sefs on 2010-03-16
Ok I found this page

[http://www.mikero.com/misc/ipcalc](http://www.mikero.com/misc/ipcalc)

which allowed me to type in the range I wanted to use and convert it to cidr for me.

Thanks.

---

### Post by capscrew on 2010-03-16
> **sefs said:**
> I made a mistake i should have said subnets instead of host.  I've corrected the initial post.

```
80/tcp       ALLOW       192.168.1.0/24
80/tcp       ALLOW       192.168.10.0/24
```

We are still talking about the same notion.  The idea of the /nn notation is to Identify the network part of the address and not the individual host.  That being so we would look for how many bits of the address would be the same.  In this case it is [FONT="Courier New"]192.168[/FONT] That would be /16 (16 bits in common).

You could use [FONT="Courier New"]192.168.0.0/16[/FONT] as a singular entry if you like.  Unfortunately this is is wider than just the 2 subnets you wish to allow.  It includes all hosts from ```
192.168.0.1 
to 192.168.255.254
```

This is 65534 hosts allowed.  Your notation allows only 508.

See [**_[COLOR="Navy"]here [/COLOR]_**]("http://www.cisco.com/en/US/tech/tk365/technologies_tech_note09186a0080093f33.shtml#subnetting")for more information about CIDR notation.

It is possible with CIDR to take a piece out of the middle.  I have tried it with the link you have located.  It works but it allows 4096 addresses.  As this system can use the 2 lines and it is for security, my feeling is: go with the 2 lines.  More secure and less confusing.

Edit:  I think it is important to emphasize that the decimal notation of the IP address is misleading.  192.168.0.0 /16 has 65534 hosts while 192.168.0.0/17 has half that amount of hosts (32766 hosts) the range is 192.168.0.1 to 192.168.127.255.

---

### Post by sefs on 2010-03-17
> **capscrew said:**
> ```
80/tcp       ALLOW       192.168.1.0/24
80/tcp       ALLOW       192.168.10.0/24
```

We are still talking about the same notion.  The idea of the /nn notation is to Identify the network part of the address and not the individual host.  That being so we would look for how many bits of the address would be the same.  In this case it is [FONT="Courier New"]192.168[/FONT] That would be /16 (16 bits in common).

You could use [FONT="Courier New"]192.168.0.0/16[/FONT] as a singular entry if you like.  Unfortunately this is is wider than just the 2 subnets you wish to allow.  It includes all hosts from ```
192.168.0.1 
to 192.168.255.254
```

This is 65534 hosts allowed.  Your notation allows only 508.

See [**_[COLOR="Navy"]here [/COLOR]_**]("http://www.cisco.com/en/US/tech/tk365/technologies_tech_note09186a0080093f33.shtml#subnetting")for more information about CIDR notation.

It is possible with CIDR to take a piece out of the middle.  I have tried it with the link you have located.  It works but it allows 4096 addresses.  As this system can use the 2 lines and it is for security, my feeling is: go with the 2 lines.  More secure and less confusing.

Edit:  I think it is important to emphasize that the decimal notation of the IP address is misleading.  192.168.0.0 /16 has 65534 hosts while 192.168.0.0/17 has half that amount of hosts (32766 hosts) the range is 192.168.0.1 to 192.168.127.255.

Thank you.  I think that you are correct in going with the two lines to get just what I need instead of cramming it up with ranges I don't need.

---

