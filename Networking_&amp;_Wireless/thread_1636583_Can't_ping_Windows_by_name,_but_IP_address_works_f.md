---
title: "Can't ping Windows by name, but IP address works fine."
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by damateem on 2010-12-03
My Windows machine can ping Ubuntu by name, but Ubuntu can only ping the Windows machine by using it's IP address.

This was working fine in both directions until I purged Samba. After purging Samba, I couldn't ping in either direction unless I used the IP address. I did some reading and found that Samba provides NetBIOS functionality that allows the machines to resolve host names without a DNS. Since I'm not running a local DNS, I decided to reinstall Samba. Unfortunately, I've not been able to restore it to full working condition.

I don't want to use hosts files as all the IP addresses are assigned automatically by DHCP.

I want to be able to access the Windows machine by name.

What can I do to figure out where the problem lies and, ultimately, fix it?

Thanks

---

### Post by endotherm on 2010-12-03
well, the samba package also includes a service called nmbd that provides naming resolution like NetBUI/NetBIOS.

when you purged samba, diid you keep a copy of your smb.conf? restoring it and rebooting may be the solution you need.

---

### Post by damateem on 2010-12-03
Unfortunately I didn't save any configuration files before purging.

Is nmbd installed with the Samba package?

Can I do something to find out if the nmbd service is running?

What can I do to narrow down the problem? At this point, I'm not sure what to try next.

Thanks

---

### Post by endotherm on 2010-12-03
try this:
```

sudo service restart nmbd
sudo service restart smbd

```

and see if that affects anything. samba works on a dynamically generated browse list so the amount of time it is up and runnning can be a factor. 

have you set your workgroup and whatnot for your samba config? 

also, try connecting to windows shares by name, rather than pinging, for now. fixing samba nameing resolution may fix ping as well, but the two occure at differant layers of teh stack, so lets focus on what is important. 

if you run 
```
smbtree -l
``` what do you get back?

---

### Post by damateem on 2010-12-03
```
sudo service restart nmbd
```

didn't work, so I moved the "restart" to the last parameter. The following shows exactly what I did. As you can see, the host name is still unresolved.

```
david@server1:~$ ping david-desktop
ping: unknown host david-desktop
david@server1:~$ sudo service restart nmbd
restart: unrecognized service
david@server1:~$ sudo service nmbd restart
nmbd start/running, process 1291
david@server1:~$ sudo service smbd restart
smbd start/running, process 1297
david@server1:~$ ping david-desktop
ping: unknown host david-desktop
david@server1:~$
```

I've not done anything to set "workgroup and whatnot". I don't remember seeing the need to set a workgroup in the how-to's that I looked at. What needs to be set?

How do I connect to a Windows share by name? I don't have much experience with Linux, so I appreciate your patience.

smbtree returns the following

```
david@server1:~$ smbtree -l
Enter david's password:
WORKGROUP
        \\SERVER1                       server1 server (Samba, Ubuntu)
                \\SERVER1\IPC$                  IPC Service (server1 server (Samba, Ubuntu))
                \\SERVER1\print$                Printer Drivers
        \\BRNC700C1
cli_start_connection: failed to connect to BRNC700C1<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
FAMILY
        \\TV
        \\TERRI-OFFICE
                \\TERRI-OFFICE\C$               Default share
                \\TERRI-OFFICE\ADMIN$           Remote Admin
                \\TERRI-OFFICE\My Pictures
                \\TERRI-OFFICE\SharedDocs
                \\TERRI-OFFICE\D$               Default share
                \\TERRI-OFFICE\IPC$             Remote IPC
        \\POOH
                \\POOH\C$               Default share
                \\POOH\CD Drive (E)
                \\POOH\ADMIN$           Remote Admin
                \\POOH\D$               Default share
                \\POOH\IPC$             Remote IPC
                \\POOH\CD Drive (F)
        \\FILE-SERVER
                \\FILE-SERVER\Shared
                \\FILE-SERVER\C$                Default share
                \\FILE-SERVER\CD Drive (E)
                \\FILE-SERVER\ADMIN$            Remote Admin
                \\FILE-SERVER\music
                \\FILE-SERVER\David
                \\FILE-SERVER\D$                Default share
                \\FILE-SERVER\IPC$              Remote IPC
                \\FILE-SERVER\video
        \\DAVID-DESKTOP
                \\DAVID-DESKTOP\IPC$            Remote IPC
                \\DAVID-DESKTOP\C$              Default share
                \\DAVID-DESKTOP\ADMIN$          Remote Admin
david@server1:~$
```

The tree correctly lists the hosts and shares on the network. BRNC700C1 is a printer. server1 is the Ubuntu server. The others are Windows.

If it can see the hosts, why can't it resolve their names?

---

### Post by endotherm on 2010-12-03
ok, from your smbtree output, nmbd is working fine, so you should be able to access a share like this:
open nautilus. hit ctrl + L so the path is editable, and enter:
```
smb://terri-office/shareddocs
```does teh share come up correctly?

it looks like your netbios/samba naming resolution is just fine. its only at the IP level (where 'ping' operates) that it doesn't work. do you really need IP level name res, or is it samba you are really interested in?

unless you set up a method for IP based LAN name resolution like a DNS server on your network, you have to rely on a service called AVAHI for name resolution. I don't trust AVAHI and don;'t use it so hopefully someone else can assist you with it. its my understanding that you just need the service installed and running (no config) to have it work, but as I said, I use a bind DNS server so....

as for setting up your workgroup, it looks like you are using the name "WORKGROUP" throughout your network, so you probably don't need to set it again, but if you are using a workgroup name other than "WORKGROUP" you will have to set it in samba. here is a good place to get started with samba:
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by damateem on 2010-12-03
I don't have a GUI installed. Everything is CLI so I can't use nautilus, but I did manage to access a Windows share using smbclient.

The intended use for this Ubuntu machine is a production LAMP server for a business that is getting internet via cable modem.

The reason I purged samba is that I was concerned about it introducing security issues. If you have thoughts on this, I'd be happy to get your opinion.

If it's secure, Samba would be nice because it would make it easier to move files between the server and other computers on the LAN.

If installing Samba on a production LAMP server is a bad idea, I'll use ftp or equivalent to move files.

Back to name resolution...

The only reason I reinstalled Samba is for the name resolution. When I access computers on the LAN using ssh, sftp, ping, etc., I want to be able to get to them by host name.

So I find myself at a fork in the road...

Path 1: Stick with NetBIOS and try to get name resolution working through Samba.

or

Path 2: Purge Samba once again and install a DNS server.

Any thoughts on which path is best?

---

### Post by endotherm on 2010-12-03
well, samba is only a security vulnerability if:
1) it is exposed on a publicly accessible server
2) you don't trust the inhabitants of the internal network, and cannot sufficiently lock it down via users and group permissions.

other than that, its just another service, so if you need it, keep it, if not remove it. 

I would probably set up a dns server, as that is the most surefire way to get IP name res (other than /etc/hosts).

---

### Post by damateem on 2010-12-03
The server will be accessible from the internet. I assume that's what you mean by "publicly available". However, it will be behind a router that will only forward http, ssh, and sftp ports to it. Is that an acceptable configuration from a security point of view?

Can you point me to a good how-to for setting up a DNS server? I'm concerned about getting the DNS server to play nicely with the DHCP server that runs on the router. Maybe that's not an issue but it's a big whole in my understanding at this point in time.

Your a huge help. Thanks!

---

### Post by endotherm on 2010-12-03
yeah, I would uninstall samba if it's on an edge server, but your port forwarding should thwart most attacks on it. 

this is where I started with DNS:[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
you will probably need a dynamic dns registeration for the outside world as well:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

remember, bind is for inside only, and ddns is for outside only. 

if you want it to integrate with automatic DHCP updates, then look at this:
[http://www.debianadmin.com/howto-setup-dhcp-server-and-dynamic-dns-with-bind-in-debian.html](http://www.debianadmin.com/howto-setup-dhcp-server-and-dynamic-dns-with-bind-in-debian.html)

---

### Post by damateem on 2010-12-04
Looks like a local DNS server is the way to go.

Do I need to makes changes to the Windows machines to get them to utilize the local DNS?

---

### Post by endotherm on 2010-12-04
> **damateem said:**
> Looks like a local DNS server is the way to go.

Do I need to makes changes to the Windows machines to get them to utilize the local DNS?
if they are statically addresses, yes, but if they are DHCP hosts, just set it in the dhcp server. be sure that you have set forwarders in your zone options file though, so that when they want a site off your domain, the dns server queries upstream and proxies the result back.

---

