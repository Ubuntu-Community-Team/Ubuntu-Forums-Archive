---
title: "How to find out more info about computers connected to my network"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by mrgoodfox on 2011-11-19
How can i find more information about computers connected to my network. Can I for example find the name of the computers connected to the network? Perhaps what operating system its running?

---

### Post by mikewhatever on 2011-11-20
The router should show a list of all connected machines, at least those with DHCP.

To find out about the OS, use nmap.

---

### Post by mrgoodfox on 2011-11-20
How do i find out what the routers ip address is to connect to (in Ubuntu of course). Is it always the gateway address?

---

### Post by Drenriza on 2011-11-20
use wireshark.

It will tell you their ip address, OS, what their currently looking at, uhmm dont know what else you would want to know.

Why do you want to know more about those connected to your own LAN in the first place? Don't you know who is on your own network?

---

### Post by mrgoodfox on 2011-11-20
I did download wireshark and started using it. Does wireshark pick up signals from the router that I'm connected to or does it pick up all signals in the air (for example if I put my wireless card in monitor mode (airmon-ng) 

I'm just learning networking and using different networking applications on Ubuntu.

---

### Post by SeijiSensei on 2011-11-20
Install the **nmap** package.  You can tell it to ping all the machines in a subnet with a simple command like 

```
nmap -sP 192.168.1.0/24
```

It also has options to probe each machine for open ports and identify the machine's OS.

You may not be able to find out the hostnames of these machines if there's no DNS server that handles name service for your internal network.  For Windows clients, you can install the **samba-common** package and use nmblookup for this task:

```
nmblookup -A 10.10.10.10
```

will query the machine at 10.10.10.10 and report its hostname and some other relevant information.

---

### Post by redmk2 on 2011-11-20
> **SeijiSensei said:**
> You may not be able to find out the hostnames of these machines if there's no DNS server that handles name service for your internal network.  For Windows clients, you can install the **samba-common** package and use nmblookup for this task:

```
nmblookup -A 10.10.10.10
```

will query the machine at 10.10.10.10 and report its hostname and some other relevant information.

Most of the time but **not all** of the time.  The tool nmblookup lists the netbios name and sufix.  The netbios name does not have to be the same as the hostname -- netbios != dns

---

### Post by Dangertux on 2011-11-20
I really hope this doesn't have to do with this thread : [http://ubuntuforums.org/showthread.php?t=1884185](http://ubuntuforums.org/showthread.php?t=1884185)

Because if it does, I'm going to let you in on a little secret. Using Wireshark to monitor network traffic of those who do not consent prior to it, Note -- utilizing an open wireless access point that does not have an acceptable use policy does NOT count as legal consent, can be considered an illegal wiretap, and can put you in prison for a hot minute.

Consider what you're doing before you do it.

---

### Post by SeijiSensei on 2011-11-20
> **redmk2 said:**
> Most of the time but **not all** of the time.  The tool nmblookup lists the netbios name and sufix.  The netbios name does not have to be the same as the hostname -- netbios != dns

You'll notice I said "for Windows clients."  On Windows machines the NetBIOS name and its DNS hostname are nearly always identical unless something strange happened with Vista/Win7 that I don't know about.  In AD-managed networks they're the same as well.

I once wrote a script to poll all the Windows machines in a network with nmap and used nmblookup to determine their NetBIOS names.  I then used the result to populate a DNS zone file.  I've also run that script on AD-managed networks, and it returns the same set of hostnames as the AD server reports.

Linux doesn't use NetBIOS names for much of anything unless you're running Samba and either make the Linux box a WINS server or advertise the Linux box to a Windows server.

---

### Post by Dangertux on 2011-11-20
> **SeijiSensei said:**
> You'll notice I said "for Windows clients."  On Windows machines the NetBIOS name and its DNS hostname are nearly always identical unless something strange happened with Vista/Win7 that I don't know about.  In AD-managed networks they're the same as well.

I once wrote a script to poll all the Windows machines in a network with nmap and used nmblookup to determine their NetBIOS names.  I then used the result to populate a DNS zone file.  I've also run that script on AD-managed networks, and it returns the same set of hostnames as the AD server reports.

Linux doesn't use NetBIOS names for much of anything unless you're running Samba and either make the Linux box a WINS server or advertise the Linux box to a Windows server.

They are not always the same because a netbios name is only 16 bytes appended by the service.

So if the FQDN is longer than 16 bytes it will be shortened.

---

### Post by cariboo on 2011-11-20
To the op of this thread, I think you have been given enough info to do what your original request in this thread asked. Any more than this, and we start getting on rather shaky legal ground.Thread closed.

---

