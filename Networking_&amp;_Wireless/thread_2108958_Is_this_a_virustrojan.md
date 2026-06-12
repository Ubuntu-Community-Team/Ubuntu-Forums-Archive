---
title: "Is this a virus/trojan ?"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by oygle on 2013-01-26
Have noticed the router logs for this computer trying to access various ports, like ..

192.168.1.101:46597 > 199.101.28.130:139 S Seq=-422340680, Ack=0 -Default Defense

192.168.1.101:55075 > 199.101.28.130:445, S Seq=-1339368640, Ack=0 -Default Defense

what would be running on Kubuntu that is trying to access those ports ?

---

### Post by Sazhen86 on 2013-01-26
That sounds like samba.  This page explains the use of ports 137, 138, 139 and 445 quite well:

[http://wiki.centos.org/HowTos/SetUpSamba](http://wiki.centos.org/HowTos/SetUpSamba)

---

### Post by oygle on 2013-01-27
> **Sazhen86 said:**
> That sounds like samba.  This page explains the use of ports 137, 138, 139 and 445 quite well:


Okay thanks. I haven't installed samba package, but I was trying to access another computer on the LAN at the time, so the IP address of the destination should have been ..

192.168.1.100:139

but it was ..

199.101.28.130:139

which is a Bigpond address, strange. There are 'bit' of samba installed by default, for example.

samba-common
samba-common-bin
libwbclient0
smbclient
libsmbclient
kdenetwork-filesharing

---

### Post by Sazhen86 on 2013-01-27
Sorry, I noticed the ports rather than the addresses.  It would be useful to know what executable is making that connection , or at least trying to make it.  Perhaps 'lsof" could be of help here.  I'm not sure if there's a way to get the firewall to log the executable, perhaps someone else knows.

---

### Post by oygle on 2013-01-27
> **Sazhen86 said:**
> Sorry, I noticed the ports rather than the addresses.

The IP address resolves to [http://www.bigpondsitehelp.com/](http://www.bigpondsitehelp.com/) , and BigPond is the ISP I use. But there was nothing in the router logs this morning for that IP. Then , I tried to access the Win XP computer from Ubuntu, by using Dolphin's location bar. Then that same IP started up, ports 139 and 445.

> **Sazhen86 said:**
> It would be useful to know what executable is making that connection , or at least trying to make it.  Perhaps 'lsof" could be of help here.  I'm not sure if there's a way to get the firewall to log the executable, perhaps someone else knows.

The router logs don't provide that level of detail. I know some windows firewall logs often have that type of details though. I ran "lsof", output was huge, nothing to tell me what was causing the request out to that IP/port.

---

### Post by Sazhen86 on 2013-01-27
Do you have the samba nmbd process running?  This is the discovery process for samba and will cause broadcasts to be sent.

---

### Post by oygle on 2013-01-28
Nothing under the name of samba in the processes. There is

kio-smb
gvfsd-smb
gvfsd-smb-browse

[Post about ports 139 and 445]("http://ubuntuforums.org/showthread.php?t=1563640")

---

### Post by Sazhen86 on 2013-01-28
The clue seems to be that you tried to access the XP computer when this happened.  You could run wireshark with a filter set to the bigpond IP and ports 445 and 139.  That will allow you to see the traffic being sent and should allow you to pipe the output of lsof to grep and look for the strings "netbios" and "microsoft".  That may allow you to catch whatever executable is making the connection.

---

### Post by oygle on 2013-01-29
Thanks, I have installed WireShark. However, when I ran it, no interfaces were showing. Possibly it has to be run as "sudo" to get the interfaces ??

Anyway, read a bit on their site, and came across a utility called dumpcap, which is already installed under Kubuntu. Used one of their examples ..

```
$ sudo dumpcap -i eth0 -a duration:60 -w Documents/output.pcap
```

and then browsed the XP share whilst that was running. Then opened that file under WireShark. There were lots of entries, but none for that BigPond IP address. So, I'm thinking that I have the wrong interface ??

Oygle

---

### Post by NilPointer on 2013-01-29
Yes, Wireshark from normal user account doesn't show interfaces because it doesn't have permissions to access them. Running it as root seems like workaround (it works, but since it's GUI network app, it's not recommended to run it as root, because if one app gets exploited, entire system is compromised). Wireshark is split in two parts - Wireshark (GUI frontend) and dumpcap (core) - if properly configured, it allows to run GUI as non-root and dumpcap as root to reduce security risks:

[http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)

---

### Post by Sazhen86 on 2013-01-29
eth0 is typically the wired ethernet connection and eth1 the wireless ethernet connection.  The ifconfig -a command will tell you which interfaces are connected and their IP addresses.

The connection to BigPond must be going out of one of them.

---

