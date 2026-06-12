---
title: "Windows network issue"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by amadeus266 on 2010-10-28
Hi all, Just installed 10.10 on my laptop and everything is working great except for an odd network browsing issue... I am in a windows network and when I open network I can see all other computers on the network but not my own. I have searched and tried a number of fixes posted around but to no avail. Is this a new issue with samba?

---

### Post by CharlesA on 2010-10-28
Do you have some form of name resolution on the network, or are the Windows machines just using NetBIOS broadcasts?

---

### Post by amadeus266 on 2010-10-28
> **CharlesA said:**
> Do you have some form of name resolution on the network, or are the Windows machines just using NetBIOS broadcasts?

I have a Windows 2003 Server for DNS and using netbios. I also have the correct workgroup set in the smb.conf.

---

### Post by CharlesA on 2010-10-28
Are you able to connect to it by typing something like:

\\ip.addess.goes.here

From a windows box?

---

### Post by amadeus266 on 2010-10-28
Yes, that does work CharlesA. But this computer does not show when browsing the network the usual way.

---

### Post by CharlesA on 2010-10-28
Does it connect if you do the same thing with the hostname?

\\hostname

Are you blocking any ports on that machine?

I recall running into a similar situation and found it was because ports 137 and 138 were being blocked and nmbd wasn't running.

---

### Post by amadeus266 on 2010-10-28
\\hostname does not work and as far as I can tell there is no firewall running.

---

### Post by CharlesA on 2010-10-28
Ok, make sure that nmbd is running. Basically it cannot find the NetBIOS name for that machine, which can be caused by nmbd not running or having those two ports blocked.

---

### Post by amadeus266 on 2010-10-28
How do I check? Sorry, I am a user, not a hacker.

---

### Post by CharlesA on 2010-10-28
If you've got console or SSH access you can run this:

```
service nmbd status
```

If it's running, it will say something like this:

```
charles@thor:~$ service nmbd status
nmbd start/running, process 956
```

EDIT: To check to see if a firewall is running, you can run this:

```
sudo iptables -L
```

---

### Post by amadeus266 on 2010-10-28
adam@adam-Inspiron-1525:~$ service nmbd status
nmbd start/running, process 1331

adam@adam-Inspiron-1525:~$ sudo iptables -L
[sudo] password for adam: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

Looks like it should be working.

---

### Post by CharlesA on 2010-10-28
That looks ok.

Does the DNS server have an entry for that machine? I know Windows doesn't add Linux machines automatically to the DNS hosts list.

---

### Post by SeijiSensei on 2010-10-28
> **CharlesA said:**
> Does the DNS server have an entry for that machine? I know Windows doesn't add Linux machines automatically to the DNS hosts list.

I'm with Charles.  Add a static A and PTR record to the DNS on the Windows server for the Linux box.  It's a lot easier than troubleshooting netbios broadcasts.  

If you do this, the laptop should have a static address within your local network.  You can either tell your DHCP server always to assign the same IP to your laptop's MAC address, or configure Ubuntu to use a static address within your network space.  If you routinely use the laptop outside your local network, configuring your local DHCP server is probably the better bet.

---

### Post by amadeus266 on 2010-10-29
I got it working but I'm not sure how. I did completely remove samba and all related components and config files, then reinstalled them, but at the time it didn't seem do work no matter what changes I made to smb.conf or nsswitch.conf and restarting many times. After shutting my laptop down overnight and starting it up this morning at work, it appears that it is working now.I made no changes to the DNS server or network that I connect to so I have no idea what fixed it. Thanks CharlesA and SeijiSensei for your input.

---

