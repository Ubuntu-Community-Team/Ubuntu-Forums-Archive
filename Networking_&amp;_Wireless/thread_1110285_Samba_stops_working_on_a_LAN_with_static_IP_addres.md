---
title: "Samba stops working on a LAN with static IP addresses. 8.10"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by JAGGEDSPHERE on 2009-03-29
When I try to set static IP addresses on my system's(2) samba stops working.  

**findsmb** reports of their existence(PC1 and PC2) but  **smbclient -L** returns a timeout, access denied 

[B]timeout connecting to 208.67.217.132:139
Connection to JESS-LAPTOP failed (Error NT_STATUS_ACCESS_DENIED)
[/B]

208.67.*.* is from opendns(which I recently set as the default dns lookup for my PC) A clue? why would samba be looking there for my smb shares??

however, when I set my IP as DHCP samba works perfectly.

I really prefer to have static IPs on my systems

Have a good day.

---

### Post by capscrew on 2009-03-29
> **JAGGEDSPHERE said:**
> When I try to set static IP addresses on my system's(2) samba stops working.  

**findsmb** reports of their existence(PC1 and PC2) but  **smbclient -L** returns a timeout, access denied 

[B]timeout connecting to 208.67.217.132:139
Connection to JESS-LAPTOP failed (Error NT_STATUS_ACCESS_DENIED)
[/B]

208.67.*.* is from opendns(which I recently set as the default dns lookup for my PC) A clue? why would samba be looking there for my smb shares??


A couple of things come to mind.  
1. What is the static address you are assigning to the host: JESS-LAPTOP?

2. Are you really trying to access a Samba share over the Internet?

Samba is a LAN based technology.  It is a well known security hazard  when exposed to the Public Internet.  On the other hand OpenDNS does provide DNS for the Public Internet.

Maybe you need some form of name service for your LAN.  

> 

however, when I set my IP as DHCP samba works perfectly.

I really prefer to have static IPs on my systems


Try using an IP address in the subnet that your DHCP server uses.  **[COLOR="Red"]Make sure this IP address is *outside* of the DHCP pool though.[/COLOR]**
> 

Have a good day.

---

### Post by JAGGEDSPHERE on 2009-03-29
1. 192.168.1.30
2. no


> **capscrew said:**
> A couple of things come to mind.  
1. What is the static address you are assigning to the host: JESS-LAPTOP?

2. Are you really trying to access a Samba share over the Internet?

Samba is a LAN based technology.  It is a well known security hazard  when exposed to the Public Internet.  On the other hand OpenDNS does provide DNS for the Public Internet.

Maybe you need some form of name service for your LAN.  


Try using an IP address in the subnet that your DHCP server uses.  **[COLOR="Red"]Make sure this IP address is *outside* of the DHCP pool though.[/COLOR]**

---

### Post by capscrew on 2009-03-29
> **JAGGEDSPHERE said:**
> 1. 192.168.1.30
2. no

And what is it when you assign the IP by DHCP?

Have you tried smbclient using the IP address?

Do you have local DNS?

This:> smbclient -L returns a timeout, access denied

timeout connecting to 208.67.217.132:139
Connection to JESS-LAPTOP failed (Error NT_STATUS_ACCESS_DENIED)

Seems to indicate no local DNS.

---

### Post by JAGGEDSPHERE on 2009-03-29
well when I set my wife's laptop to have a DHCP address of **192.168.1.100** it can access smb on my computer which still has a statically assigned address of **192.168.1.10**

**smbclient -L 192.168.1.100**
returns:
[B]Domain=[JESS-LAPTOP] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (jess-laptop server (Samba, Ubuntu))
	share           Disk      
	sharejess       Disk      
	rhome           Disk      
	jess-backup     Disk      
Domain=[JESS-LAPTOP] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            R
[/B]

so it looks like I need to have some local DNS
How do I do that?

Thank you so much by the way...
:)

> **capscrew said:**
> And what is it when you assign the IP by DHCP?

Have you tried smbclient using the IP address?

Do you have local DNS?

This:

Seems to indicate no local DNS.

---

### Post by capscrew on 2009-03-29
The easiest way for a small network is to use the hosts file.  On the Ubuntu machine this is: ```
/etc/hosts
```  The comparable  file on a Windows XP is at ```
C:\WINDOWS\system32\drivers\etc\hosts
```

My /etc/host file looks like this:```
127.0.0.1 localhost
192.168.1.12 malibu
192.168.1.2  newport
192.168.1.200 printer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

The host .12 is malibu, my Ubuntu computer and .2 is an XP host.  The last one is a networked printer

All we are doing her is mapping the IP address to a hostname.  In your case you need to add yours and your wifes computers to both hosts files.  There is no centralized DNS server in this setup.

If you were to have a larger network you would use a DNS server.  But, you still are only mapping IP to name.

Does this help?

**Edit:** Only the computer(s) that are hosting shares need to have static addresses.  Only the clients accessing the shares need to have the hosts file updated.

---

### Post by JAGGEDSPHERE on 2009-03-29
OK, so I edited the hosts files on each of my computers so they could see each other's shares. on the cli all seems ok for both.

**smbclient -L JESS-LAPTOP**

returns:

[B]Domain=[JESS-LAPTOP] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (jess-laptop server (Samba, Ubuntu))
	share           Disk      
	sharejess       Disk      
	rhome           Disk      
	jess-backup     Disk      
Domain=[JESS-LAPTOP] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            
[/B]

but when I fire up nautilus and try to open the network I get a time out with no results...

---

### Post by capscrew on 2009-03-29
> but when I fire up nautilus and try to open the network I get a time out with no results...

This is most likely a not a DNS problem, but more a matter of how you made the shares.  How did you make the shares?

---

### Post by JAGGEDSPHERE on 2009-03-29
right click the file in nautilus ->properties -> share tab
set the share, and allow others to write to

---

### Post by capscrew on 2009-03-29
have you ever been able to see  the workgroup or shares?

---

### Post by JAGGEDSPHERE on 2009-03-29
hmm...well now I can access the shares from both computers.
perhaps that did it!
I think this problem is solved. 
thank you very large

---

### Post by capscrew on 2009-03-29
Then what you had last was the delay in the master browser.  Glad it all worked out!

-Cappy

---

