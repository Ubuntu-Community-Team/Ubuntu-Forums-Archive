---
title: "Hostname not announced with static network interface"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by Aleksandersen on 2010-09-17
Hi

My /etc/hostname is not announced on the local network (not showing up on my Mac nor router) when setting /etc/network/interfaces to:```
iface eth0 inet static
  address	10.0.0.10
  netmask	255.255.255.0
  gateway	10.0.0.1
```
I have tried bringing the interface up and down, and have also rebooted. If I change it to DHCP it will display, but this does not really help me.

Anyone?

---

### Post by redmk2 on 2010-09-17
> **Aleksandersen said:**
> Hi

My /etc/hostname is not announced on the local network (not showing up on my Mac nor router) when setting /etc/network/interfaces to:```
iface eth0 inet static
  address	10.0.0.10
  netmask	255.255.255.0
  gateway	10.0.0.1
```
I have tried bringing the interface up and down, and have also rebooted. If I change it to DHCP it will display, but this does not really help me.

Anyone?

Have you tried pinging this host by name.  Where is DNS for the LAN configured.  If it is the router, there should be a place for you to manually add the IP to hostname mapping.

Edit:  An alternative is to use the /etc/hosts file on each machine for this.

---

### Post by Aleksandersen on 2010-09-17
> **redmk2 said:**
> Have you tried pinging this host by name.
ping: cannot resolve webapps: Unknown host

Pinging by the static IP address works.
> **redmk2 said:**
> Where is DNS for the LAN configured.  If it is the router, there should be a place for you to manually add the IP to hostname mapping.
That is on the router. There is a field to set this manually, but I have not had to do this with the Windows-PC and the Mac. Both of them are setup to use static addresses as well, so I would prefer to have my Linux setup work the same way.

I am only assuming this is possible. It works when using DHCP, so it is probably just a setting somewhere that I have overlooked.

---

### Post by redmk2 on 2010-09-17
> **Aleksandersen said:**
> ping: cannot resolve webapps: Unknown host

That is on the router. There is a field to set this manually, but I have not had to do this with the Windows-PC and the Mac. Both of them are setup to use static addresses as well, so I would prefer to have my Linux setup work the same way.

I am only assuming this is possible. It works when using DHCP, so it is probably just a setting somewhere that I have overlooked.
As far as I know there is no automagic setting to broadcast the hostname to IP mapping in Linux.  The hostname can be resolved locally if it is mapped in the /etc/hostname file and globally if in a DNS server database.  Using DHCP may add the entry to the DNS database if DHCP is configured to do so.

If you router's DNS server picks up the information from the DHCP  server or has a way of polling the hosts on the LAN that would be something to configure in the router not in Ubuntu.

Once again hostnames are not broadcast.  The are a mapping in a database that is referenced.

**Edit:**Out of curiosity; Are these names really hostnames or maybe FQDN such as *hostname*.local?  If so this is done by Bonjour on Apple and Avahi on Linux hosts.  The protocol is mDNS.

---

### Post by SeijiSensei on 2010-09-17
Hostnames are never advertised on the network by default in the *nix world.  You need to have an entry for the host on your DNS server.

Windows handles this problem differently with SMB (aka "Windows networking").  You could run samba on your machine so that its nmbd program will broadcast the name to other Windows hosts.  The better solution is to add an entry in your DNS server for this host.

---

### Post by Aleksandersen on 2010-09-17
I don&#8217;t have Samba running on my Mac. Bonjour (mDNS) is probably running, though.

---

### Post by redmk2 on 2010-09-17
> **SeijiSensei said:**
> Hostnames are never advertised on the network by default in the *nix world.  You need to have an entry for the host on your DNS server.

Windows handles this problem differently with SMB (aka "Windows networking").  You could run samba on your machine so that its nmbd program will broadcast the name to other Windows hosts.  The better solution is to add an entry in your DNS server for this host.

Samba does not broadcast hostnames.  It will broadcast **NetBIOS **names though.  It would not be correct to run Samba just to provide naming services in the LAN.

---

### Post by SeijiSensei on 2010-09-17
> **redmk2 said:**
> Samba does not broadcast hostnames.  It will broadcast **NetBIOS **names though.  It would not be correct to run Samba just to provide naming services in the LAN.

In mixed networks where DNS is provided by a Windows Active Directory server netbios names and DNS hostnames are usually identical.  I couldn't tell if he was working on a Windows network, in which case advertising via nmbd will help.  He didn't give us any information on how DNS is structured in the network he is using.

If it's just his Ubuntu box, a Mac, and a router, then I agree, this technique won't help.

---

### Post by redmk2 on 2010-09-18
> **SeijiSensei said:**
> In mixed networks where DNS is provided by a Windows Active Directory server netbios names and DNS hostnames are usually identical.  
Only in the sense that they are the same characters (up to the first 15) and can be perceived as the the same by humans.  Thats as far as it goes.  

Windows Active Directory manages DNS in the same way as BIND.  All windows machines broadcast their COMPUTER NAME as a NetBIOS name.  NetBIOS has nothing to do with AD. Perhaps you are confusing NetBIOS over TCP (NBT) with the SMB protocol. 

**Hostnames** are defined in *nix based systems in /etc/hostname.  The /etc/hosts file *maps this hostname to a network interface *of the host.  DNS consolidates these names in a centralized data base.   

**NetBIOS **names are not defined in /etc/hosts at all.  The mapping can be handled in numerous ways.  But in the end it has more to do with identifying the hosts capabilities.  A windows share (SMB resource) is only one of those.  See [**_here _**]("http://support.microsoft.com/kb/163409")for a list of identifiers.

In the end, just because things look the same or appear to have the same purpose doesn't make them the same.

> 
I couldn't tell if he was working on a Windows network, in which case advertising via nmbd will help.  
Not with mapping hostnames to IP addresses.  From the nmbd man pages:```
nmbd is a server that understands and can **[COLOR="Red"]reply to netbios name service requests[/COLOR]**, like those produced by LanManager.
```> 
He didn't give us any information on how DNS is structured in the network he is using.
The Op was explicitly asking about broadcasts of hostnames.  There is no 1 to 1 relationship between hostnames/DNS and NetBIOS names.> 

If it's just his Ubuntu box, a Mac, and a router, then I agree, this technique won't help.
Right, but we have needlessly wandered down the NetBIOS road.

---

### Post by HiFiJive on 2010-12-14
Please correct me if I'm wrong, but I do not think what he's trying will actively advertise his ubuntu box's hostname because it's not registering it's hostname during the DHCP process. If you can create a static record and attach a c-name to it in your router's setup that should work. Another option may be to create what some routers call a "host reservation" which *usually* requires you to type in a mac address of the interface that will be requesting an IP from DHCP and the IP address you desire DHCP to assign. DHCP will usually register its hostname being advertised and hand out the reserved IP you set. 

This is assuming you are doing your name resolution on your router. Easy test: 
on both your ubuntu and mac machines run this in terminal.

```
PROMPT$: nslookup localhost
Server:		11.22.33.44
Address:	11.22.33.44#53

Non-authoritative answer:
Name:	localhost
Address: 127.0.0.1
```
In the example above 11.22.33.44 is the name resolution server from which your ubuntu box must be registered with. If this points to the IP address of your router, then try my suggestion above.

---

