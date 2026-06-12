---
title: "Samba client problem"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by stardustdk on 2009-10-28
Hey all.

I am trying to setup my Ubuntu 9.04 as a Samba client, and found

this:

> [global]
workgroup = WORKGROUP
netbios name = computername
server string =
name resolve order = bcast host lmhosts wins
preferred master = no
os level = 20

I did not work for me to start Windows network and se the shared directory on the server.

Two things is working, though:

FTP to 192.168.1.2 and connecting to the server using the same IP and shared dir name.

Trying to connect using the servers servername don't work.

Smbfs is installed.

Help wanted.

Best regards

Stardustdk

---

### Post by Iowan on 2009-10-28
Hopefully, [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To will be helpful.

---

### Post by ant2ne on 2009-10-28
> **stardustdk said:**
> 
Two things is working, though:

FTP to 192.168.1.2 and connecting to the server using the same IP and shared dir name.

Trying to connect using the servers servername don't work.
You say, "Trying to connect using the servers servername" are you tring to connect ftp here? At this description it sounds like a DNS problem.

Can you ping the server by ip? In terminal type...
ping 192.168.1.2
Can you pin the server by name? In terminal type...
ping *servername*

ALSO remember with samba, (any sharing, really) you have got to have permissions on the share you are connecting to. You need samba permissions (in smb.conf) AND file system permissions.

---

### Post by stardustdk on 2009-10-29
Iowan: 

I found it myself and no go :(.

ant2ne:

ping 192.168.1.2 works.
ping *servername* does not.


When I use the "connect to server" and use IP number and share map name - no problems.

When I try to use the network option, I can see my laptop on the workgroup, not the server.

---

### Post by stardustdk on 2009-10-29
Now I can see the server in the workgroup, but not the share dir??

---

### Post by swerdna on 2009-10-29
Three things you might check:
[LIST=1]
[*]the workgroup names are the same on all machines
[*]run ```
sudo /etc/init.d/samba status
```and see if you get a response that smbd and nmbd are running
[*]check there isn't a proprietary firewall blocking samba on the windows box (they usually block samba unless you open it for samba)
[/LIST]

---

### Post by stardustdk on 2009-10-29
swerdna:

Point 1: Check
Point 2: Check, smbd and nmbd are running.
Point 3: Don't know by now, it is a Windows 2008 server running a workgroup.
Are not MS expert, so I have to ask an expert.

---

### Post by dmizer on 2009-10-29
> **stardustdk said:**
> Iowan: 

I found it myself and no go :(.

Was there something in particular that was giving you problems? Any specific error you encountered after running through the howto?

What's the output of:
```
smbtree
```

---

### Post by stardustdk on 2009-10-29
Output of smbtree:

> WORKGROUP
	\\SERVER         		
	\\LG-LAPTOP      		
		\\LG-LAPTOP\IPC$           	IPC Service ()

---

### Post by ant2ne on 2009-10-29
> **stardustdk said:**
> Iowan: 
ant2ne:

ping 192.168.1.2 works.
ping *servername* does not.


When I use the "connect to server" and use IP number and share map name - no problems. So you CAN connect with \\192.168.1.2\sharename but not \\servername\sharename ?  That is a DNS issue. What are you using for DNS?

---

### Post by Iowan on 2009-10-29
Quick/dirty fix is to edit */etc/hosts* file and add IP address/hostname pair.  This doesn't work well for DHCP addresses.

---

### Post by dmizer on 2009-10-29
Are both computers Linux or is one of them Windows?

---

### Post by stardustdk on 2009-10-29
One (the server) is actual a MS server 2008 set up by a friend. That is done due to my Raid 5 controller. My ubuntu is set up as a client, now with the smb.conf looking like this:

> [global]
workgroup = WORKGROUP
netbios name = LG-Laptop
server string =
name resolve order = lmhosts wins bcast host
preferred master = no
os level = 20

and
> 
sudo ufw allow proto udp to any port 137 from 192.168.1.0/24
sudo ufw allow proto udp to any port 138 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.1.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.1.0/24

So???

---

### Post by stardustdk on 2009-10-29
ifconfig -a - wlan:

wlan0     Link encap:Ethernet  HWaddr 00:18:de:c1:23:72  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fec1:2372/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164606 (164.6 KB)  TX bytes:31483 (31.4 KB)

---

### Post by dmizer on 2009-10-29
Please post the contents of /etc/nsswitch.conf and the output of:
```
sudo /etc/init.d/winbind status
```

Have you tried completely disabling UFW? Are there any other firewalls involved, and if so, have you tried disabling them?

---

### Post by stardustdk on 2009-10-30
> 

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

And:
> 
* winbind is running

I have tried without ufw running.


It **might** be solved as I can get to the shared dir after 10-15 minutes waiting.

I got advised to open the 3 ports: 145,146 and 147 as well.

---

### Post by ant2ne on 2009-10-30
> **ant2ne said:**
> So you CAN connect with \\192.168.1.2\sharename but not \\servername\sharename ?  That is a DNS issue. What are you using for DNS?
Not sure why my statement is getting ignored. You connect with no problem when using IP but have a problem when using names, this is a DNS issue. *confused*

---

### Post by stardustdk on 2009-10-31
DNS: No issue, I "just" have to wait 10-15 minutes?! (Confuse me!)
**Then** I can use servername/sharename..

Enlight me please why I have to wait so long, router??

---

### Post by dmizer on 2009-11-01
> **stardustdk said:**
> DNS: No issue, I "just" have to wait 10-15 minutes?! (Confuse me!)
**Then** I can use servername/sharename..

Enlight me please why I have to wait so long, router??

Do you use OpenDNS?

---

### Post by ant2ne on 2009-11-01
> **stardustdk said:**
> DNS: No issue, I "just" have to wait 10-15 minutes?! (Confuse me!)
**Then** I can use servername/sharename..

Enlight me please why I have to wait so long, router??
Something is wrong with your DNS.

I'm thinking this is wrong
> 
[global]
workgroup = WORKGROUP
netbios name = computername
server string =
name resolve order = bcast host lmhosts wins
preferred master = no
os level = 20 


try
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bk1
then sudo nano /etc/samba/smb.conf
and modify line 'name resolve order'
and put hosts in first. Then see what happens.

---

### Post by swerdna on 2009-11-01
Could be this is the problem:> Point 3: Don't know by now, it is a Windows 2008 server running a workgroup.
Is it set up to require 2008 server authentication and access?

---

### Post by dmizer on 2009-11-02
> **ant2ne said:**
> try
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bk1
then sudo nano /etc/samba/smb.conf
and modify line 'name resolve order'
and put [COLOR="Red"]hosts[/COLOR] in first. Then see what happens.

No, it should be "host" not "hosts", and the line should be formatted like so:
```
   name resolve order = lmhosts wins bcast host
```
Unless:
> **swerdna said:**
> Is it set up to require 2008 server authentication and access?
Where the 2008 server is also a DNS server. In which case the above line should be simply commented out.

---

### Post by stardustdk on 2009-11-03
Is it set up to require 2008 server authentication and access?

No I don't have to use username/pass.

---

