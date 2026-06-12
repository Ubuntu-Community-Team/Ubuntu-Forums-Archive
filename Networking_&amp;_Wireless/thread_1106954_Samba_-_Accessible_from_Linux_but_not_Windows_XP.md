---
title: "Samba - Accessible from Linux but not Windows XP"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by TheFuzzy0ne on 2009-03-26
Hi everyone.

I'm trying to get Samba or NFS running. I think I was in way over my head with getting NFS to work from Windows, so I tried Samba.

The Samba server is on a dedicated box, and I can mount a share with no problems from within Kubuntu on my machine, but I can't from within Windows.

I'm running Vuurmuur on my server, which doesn't even see a connection from my Windows installation, but it shows my connection from my Kubuntu installation.

I've disabled all firewalls, anti-virus etc on my Windows box (including Windows' own firewall). I can ping the netbios name "server" with no problems, or the domain name server.home with no problems.

Both Windows and Kubuntu are on the same box, and both have the same IP address, however, I can't mount my Samba share from within Windows using any of the following:
//server/web
//server.home/web
//192.168.1.70/web
all of which work from my Linux box.

(Obviously I put the slashes the other way for my Windows installation).

Can anyone help?

Thanks in advance.

EDIT:

I get a load of lines like this in my syslog:

Mar 26 13:42:07 hope kernel: vrmr: DROP out policy IN= OUT=eth1 SRC=192.168.1.70 DST=198.41.0.4 LEN=79 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=53 LEN=59

This no doubt has something to do with vuurmuur, but I don't know what exactly, since it works from my Linux box.

---

### Post by fiuwe on 2009-03-26
Can you see it from Windows ?
If not, did you set correctly the workgroup in which it has to work ?
In my Ubuntu it is set as default as "WORKGROUP" and i could not connect to it because the Windows Workgroup is writtten in this way "Workgroup"... 


Have you set any account user for it ?

Usually i left open the Guess Access for the shared SAMBA folders .

In that way i have no problem to connect to them...

---

### Post by TheFuzzy0ne on 2009-03-26
Hello, and thanks for your reply. I was have been playing around with my server's firewall settings, and messing around with Samba's configuration file, and now it seems to work on my Windows box. I've got no explanation as to why, but I noticed that the firewall (Vuurmuur) on my server was dropping smb requests from Windows boxes. Everything I'd set up through Vuurmuur previously, was still working  - http, https, ssh, ping etc... However, I don't pretend to understand a great deal about IP Tables, and even with a GUI as great as Vuurmuur's, I still get a bit lost. I purged Vuurmuur, and re configured it again from scratch, and it seems to work fine now. 

I can only conclude that it may have been something to do with a single setting in the previous firewall configuration, or that it might have been an issue with netbios, as I was unable to ping the netbios name from my Windows box, but now I can.

Just to be sure, I added the netbios name to my Windows hosts file (C:\Windows\system32\drivers\etc\hosts):
```

192.168.1.70 server

```

I strongly suspect that this may have fixed the problem to begin with, although at the time Windows was unable to locate the server share, even when I tried to access the server through an IP address as opposed to hostname.

Thanks again for taking the time to help.

---

