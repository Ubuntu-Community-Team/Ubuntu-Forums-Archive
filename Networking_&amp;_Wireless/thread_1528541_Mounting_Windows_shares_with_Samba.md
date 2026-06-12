---
title: "Mounting Windows shares with Samba"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by Pi-Rat on 2010-07-10
I'm having a problem very similar to this on-going thread of not being able to mount shares (I'm watching that thread, but having slightly different issues, plus I don't want to hijack his help thread):
[http://ubuntuforums.org/showthread.php?t=1528436](http://ubuntuforums.org/showthread.php?t=1528436)

I'm trying to network my Ubuntu laptop to my WinXP desktop. I'm wanting to be able to share files back-and-forth but I keep hitting problem after problem. Been able to share the printer connected to the XP box just fine, but not the shared folder and external drive.

I followed the steps here, but the mounting step fails:
[http://julien.herbin.ecranbleu.org/samba_client_howto/](http://julien.herbin.ecranbleu.org/samba_client_howto/)

I have tried the following commands:
```
sudo mount -t smbfs //SEPCom/SharedDocs /mnt/SharedDocs_on_SEPCom

```
Host didn't resolve, so did network IP
```
sudo mount -t smbfs //129.168.2.2/SharedDocs /mnt/SharedDocs_on_SEPCom

```
 Then I get this:
```
mount error(110): Connection timed out
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Tried this:
```
sudo mount -o smbfs //129.168.2.2/SharedDocs /mnt/SharedDocs_on_SEPCom

```
Then
```
sudo mount -t cifs //129.168.2.2/SharedDocs /mnt/SharedDocs_on_SEPCom

```

All have that time out message. Tried with my firewall on and off. The XP box is up and running and connected to the network AND the internet.

So other than the printer, neither system sees or knows about each other. Any ideas on what I should try next?

---

### Post by Iowan on 2010-07-10
I appreciate your keeping *similar* problems in separate threads. [This]("http://ubuntuforums.org/showpost.php?p=9574156&postcount=8") post from the referenced thread might be useful for starters. (Looks like you've already tried it)
[This]("http://ubuntuforums.org/showthread.php?t=288534") How-To is getting old, but *might* still hold some useful information.

---

### Post by capscrew on 2010-07-10
> **Pi-Rat said:**
> I'm having a problem very similar to this on-going thread of not being able to mount shares (I'm watching that thread, but having slightly different issues, plus I don't want to hijack his help thread):
[http://ubuntuforums.org/showthread.php?t=1528436](http://ubuntuforums.org/showthread.php?t=1528436)

I'm trying to network my Ubuntu laptop to my WinXP desktop. I'm wanting to be able to share files back-and-forth but I keep hitting problem after problem. Been able to share the printer connected to the XP box just fine, but not the shared folder and external drive.

I followed the steps here, but the mounting step fails:
[http://julien.herbin.ecranbleu.org/samba_client_howto/](http://julien.herbin.ecranbleu.org/samba_client_howto/)

I have tried the following commands:
```
sudo mount -t smbfs //SEPCom/SharedDocs /mnt/SharedDocs_on_SEPCom

```
Host didn't resolve, so did network IP
```
sudo mount -t smbfs //129.168.2.2/SharedDocs /mnt/SharedDocs_on_SEPCom

```
 Then I get this:
```
mount error(110): Connection timed out
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Tried this:
```
sudo mount -o smbfs //129.168.2.2/SharedDocs /mnt/SharedDocs_on_SEPCom

```
Then
```
sudo mount -t cifs //129.168.2.2/SharedDocs /mnt/SharedDocs_on_SEPCom

```

All have that time out message. Tried with my firewall on and off. The XP box is up and running and connected to the network AND the internet.

So other than the printer, neither system sees or knows about each other. Any ideas on what I should try next?

What do the logs say about this.  The error logs are at /var/log/samba.  I'm not near a Linux host so I can't advise specifically, but I would muck about there first.

---

### Post by Pi-Rat on 2010-07-10
Thanks for the replies. Tried the man page, but it's rather confusing. So I tried the following commands:
```
sudo mount.cifs //192.186.2.2/SharedDocs /mnt/SharedDoc_on_SEPCom
```
And got this:
```
mount error: can not change directory into mount target /mnt/SharedDoc_on_SEPCom
```

This means nothing to me, except the man page gave me the idea that I'd have to create a mount point. Or something... (?) :confused:

There are 10 logs showing up: log.buntop, log.__ffff_192.168.2.2  log.sepcom, log.0.0.0.0, log.__ffff_127.0.0.1, log.__ffff_192.168.2.4, log.smbd, log.192.168.2.2, and log.__ffff_127.0.1.1  log.nmbd.

Here's bits and pieces of the logs (only cutting out repeated attempts as they show the same thing, but the time stamps of all the tries I've done):

```
[2010/07/10 21:27:47,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/10 21:27:47,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```

```
[2010/07/10 18:47:45,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/10 18:47:45,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```

```
2010/07/07 01:36:46,  0] smbd/map_username.c:140(map_username)
  can't open username map /etc/samba/smbusers. Error No such file or directory
```

```
[2010/07/06 23:30:59,  0] lib/util_sock.c:738(write_data)
[2010/07/06 23:30:59,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2010/07/06 23:30:59,  0] smbd/process.c:62(srv_send_smb)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
```

This one includes all tries for a given session (including typo'd tries, wrong command structures, etc):
```
[2010/07/10 15:38:47,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
[2010/07/10 15:38:47,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
[2010/07/10 15:38:47,  0] nmbd/nmbd.c:330(reload_interfaces)
  reload_interfaces: No subnets to listen to. Waiting..
[2010/07/10 19:04:14,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
[2010/07/10 19:04:14,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(137) ERRNO=Network is unreachable
[2010/07/10 19:04:14,  0] nmbd/nmbd_packets.c:158(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.2.255 port 137 failed
[2010/07/10 19:04:14,  0] nmbd/nmbd_namequery.c:244(query_name)
  query_name: Failed to send packet trying to query name RATSNEST<1d>
[2010/07/10 19:04:14,  0] nmbd/nmbd.c:330(reload_interfaces)
  reload_interfaces: No subnets to listen to. Waiting..
[2010/07/10 19:23:16,  0] nmbd/nmbd.c:71(terminate)
  Got SIGTERM: going down...
[2010/07/10 19:24:17,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/10 19:38:56,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
[2010/07/10 19:38:56,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(137) ERRNO=Network is unreachable
[2010/07/10 19:38:56,  0] nmbd/nmbd_packets.c:158(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.2.255 port 137 failed
[2010/07/10 19:38:56,  0] nmbd/nmbd_namequery.c:244(query_name)
  query_name: Failed to send packet trying to query name RATSNEST<1d>
[2010/07/10 19:38:56,  0] nmbd/nmbd.c:330(reload_interfaces)
  reload_interfaces: No subnets to listen to. Waiting..
[2010/07/10 21:04:57,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server BUNTOP is now a local master browser for workgroup RATSNEST on subnet 192.168.2.4
  
  *****
```

```
[2010/07/10 20:55:45,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2010/07/10 21:27:47,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
```

Mean anything to anybody reading this?


EDIT: I ran an nmap scan on the desktop to see if I could get some further info. This is what I got back:

```
Not shown: 996 closed ports
PORT     STATE SERVICE      VERSION
135/tcp  open  msrpc        Microsoft Windows RPC
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds Microsoft Windows XP microsoft-ds
2869/tcp open  http         Microsoft HTTPAPI httpd 1.0 (SSDP/UPnP)
|_html-title: Site doesn't have a title (text/html).
MAC Address: 00:13:D4:7A:8D:9D (Asustek Computer)
Device type: general purpose
Running: Microsoft Windows XP
OS details: Microsoft Windows XP SP2 or SP3, or Windows Server 2003
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=252 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows

Host script results:
| nbstat:  
|   NetBIOS name: SEPCOM, NetBIOS user: <unknown>, NetBIOS MAC: 00:13:d4:7a:8d:9d
|   Names
|     SEPCOM<00>           Flags: <unique><active>
|     RATSNEST<00>         Flags: <group><active>
|     SEPCOM<20>           Flags: <unique><active>
|_    RATSNEST<1e>         Flags: <group><active>
|_smbv2-enabled: Server doesn't support SMBv2 protocol
| smb-os-discovery:  
|   OS: Windows XP (Windows 2000 LAN Manager)
|   Name: RATSNEST\SEPCOM
|_  System time: 2010-07-10 22:10:38 UTC-5

HOP RTT     ADDRESS
1   2.50 ms 192.168.2.2
```

Think these two lines are showing the problem?
|_smbv2-enabled: Server doesn't support SMBv2 protocol
| smb-os-discovery:

---

### Post by ST3ALTHPSYCH0 on 2010-07-10
Have you tried the "connect to server" option under places?
Choose "Windows share" in the drop down box
Server: Remote Pc (network name or IP)
Share: Network share name of shared folder
folder: leave blank
Username:windows username
domain: windows machine name


When I was running Karmic, this was the only way my Win7 machine and Ubuntu machine would play nicely. BTW, you can also make a launcher and leave it on the desktop.

---

### Post by Pi-Rat on 2010-07-10
> **ST3ALTHPSYCH0 said:**
> Have you tried the "connect to server" option under places?
Choose "Windows share" in the drop down box
Server: Remote Pc (network name or IP)
Share: Network share name of shared folder
folder: leave blank
Username:windows username
domain: windows machine name


When I was running Karmic, this was the only way my Win7 machine and Ubuntu machine would play nicely. BTW, you can also make a launcher and leave it on the desktop.

I can't find anything with "Places." I've got the netbook remix, so I see a menu on the side instead of the traditional desktop. Know where that got moved to?

---

### Post by capscrew on 2010-07-11
> **Pi-Rat said:**
> Thanks for the replies. Tried the man page, but it's rather confusing. So I tried the following commands:
```
sudo mount.cifs //192.186.2.2/SharedDocs /mnt/SharedDoc_on_SEPCom
```
And got this:
```
mount error: can not change directory into mount target /mnt/SharedDoc_on_SEPCom
```

This means nothing to me, except the man page gave me the idea that I'd have to create a mount point. Or something... (?) :confused:

> Well I don't know about creating a mount point...  It really depends on how you call the upon the SMB resource (the share).  If you browse via the Nautilus GUI then the mount point is automatically made at ~/.gvfs.  This is a hidden directory in you home directory).

There are 10 logs showing up: log.buntop, log.__ffff_192.168.2.2  log.sepcom, log.0.0.0.0, log.__ffff_127.0.0.1, log.__ffff_192.168.2.4, log.smbd, log.192.168.2.2, and log.__ffff_127.0.1.1  log.nmbd.

Here's bits and pieces of the logs (only cutting out repeated attempts as they show the same thing, but the time stamps of all the tries I've done):

```
[2010/07/10 21:27:47,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/10 21:27:47,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected [COLOR="Red"]<-- 
    This usually means that the share couldn't be found[/COLOR]
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```

```
[2010/07/10 18:47:45,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/10 18:47:45,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```

```
2010/07/07 01:36:46,  0] smbd/map_username.c:140(map_username)
  can't open username map /etc/samba/smbusers. Error No such file or directory[COLOR="red"]<-- 
   This is why the share can't be found[/COLOR] 
``` 

```
[2010/07/06 23:30:59,  0] lib/util_sock.c:738(write_data)
[2010/07/06 23:30:59,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected [COLOR="red"]<--
    Because there isn't a share[/COLOR]
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2010/07/06 23:30:59,  0] smbd/process.c:62(srv_send_smb)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
```

This one includes all tries for a given session (including typo'd tries, wrong command structures, etc):
```
[COLOR="red"]This is the name service  resolving netbios names[/COLOR]
[2010/07/10 15:38:47,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
[2010/07/10 15:38:47,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
[2010/07/10 15:38:47,  0] nmbd/nmbd.c:330(reload_interfaces)
  reload_interfaces: No subnets to listen to. Waiting..
[2010/07/10 19:04:14,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
[2010/07/10 19:04:14,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(137) ERRNO=Network is unreachable
[2010/07/10 19:04:14,  0] nmbd/nmbd_packets.c:158(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.2.255 port 137 failed
[2010/07/10 19:04:14,  0] nmbd/nmbd_namequery.c:244(query_name)
  query_name: Failed to send packet trying to query name RATSNEST<1d>
[2010/07/10 19:04:14,  0] nmbd/nmbd.c:330(reload_interfaces)
  reload_interfaces: No subnets to listen to. Waiting..
[2010/07/10 19:23:16,  0] nmbd/nmbd.c:71(terminate)
  Got SIGTERM: going down...
[2010/07/10 19:24:17,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/10 19:38:56,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(138) ERRNO=Invalid argument
[2010/07/10 19:38:56,  0] libsmb/nmblib.c:834(send_udp)
  Packet send failed to 192.168.2.255(137) ERRNO=Network is unreachable
[2010/07/10 19:38:56,  0] nmbd/nmbd_packets.c:158(send_netbios_packet)
  send_netbios_packet: send_packet() to IP 192.168.2.255 port 137 failed
[2010/07/10 19:38:56,  0] nmbd/nmbd_namequery.c:244(query_name)
  query_name: Failed to send packet trying to query name RATSNEST<1d>
[2010/07/10 19:38:56,  0] nmbd/nmbd.c:330(reload_interfaces)
  reload_interfaces: No subnets to listen to. Waiting..
[2010/07/10 21:04:57,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  [COLOR="red"] Announcement that the host BUNTOP holds the 
list of shares for the workgroup  RATSNEST
All the hosts are in the 192.168.2.0/24 range[/COLOR]
  Samba name server BUNTOP is now a local master browser for workgroup RATSNEST on subnet 192.168.2.4
  
  *****
```

```
[2010/07/10 20:55:45,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected [COLOR="red"]<-- still no share[/COLOR]
[2010/07/10 21:27:47,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
```

Mean anything to anybody reading this?
See my notes in red.  You need to set up Samba correctly.  How did you go about setting up Samba?  As @Morbius1 has said many times before -- Please post the output of the following commands:

```
net usershare info 
sudo net usershare info
testparm -s
```

---

### Post by ST3ALTHPSYCH0 on 2010-07-11
Alright, after installing UNR in a VM and digging here's the answer:
Connect to server is in the file menu in the file browser.

---

### Post by Pi-Rat on 2010-07-11
Thank you all for your help. I got tired and frustrated and went to bed last night after my last post. I decided to turn off both machines overnight. When I got up I tried the mount.cifs again. It worked this time. How/why did THAT work?
This is the page I used to configure everything:
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

As for the commands this is what shows:
```
susan@BUNTop:~$ net usershare info
susan@BUNTop:~$ sudo net usershare info
[sudo] password for susan: 
susan@BUNTop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Processing section "[K]"
Processing section "[SharedDocs]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = RATSNEST

[homes]
	read only = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Documents]
	path = /home/susan/Documents
	valid users = susan
	read only = No

[K]
	path = /mnt/K_on_SEPCom
	valid users = susan

[SharedDocs]
	path = /mnt/SharedDocs_on_SEPCom
	valid users = susan
	read only = No


```

Think it finally restarted the samba server or something? Or just frustration and tiredness claiming another brain? :-k

---

