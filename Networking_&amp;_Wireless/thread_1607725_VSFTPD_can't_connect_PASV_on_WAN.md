---
title: "VSFTPD can't connect PASV on WAN"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by amanisdude on 2010-10-28
Hi all,

I'm having a peculiar problem.  I have VSFTPD working and everything works great on my local network!  The only problem is that I can't get PASV mode to work over the WAN.  

I've tried everything: 
- making sure the *pasv_enable*, *pasv_min_port*, and *pasv_max_port* variables are set in vsftpd.conf
- punching holes in Shorewall for these ports via rules
- setting up port forwarding for these ports in my routers (although this might be unnecessary)

The problem, is PASV mode works fine when I access from either router (my server is behind two routers  ^_^"), but not from my WAN IP.  Could this be a problem with my ISP?

Any help would be appreciated.  Thanks kindly!

EDIT:  I should add that I am using Comcast (residential) in northern California

---

### Post by amanisdude on 2010-10-29
Let's try bumpin' this piece!

Also, to add some more detail, yes, clients can connect to VSFTPD via port 21 over the WAN.  The process just hangs when the client switches to passive mode and requests LIST.  Here's a standard transaction log: 

```
Thu Oct 28 16:47:56 2010 [pid 2] CONNECT: Client "<CLIENT IP>"
Thu Oct 28 16:47:57 2010 [pid 2] FTP response: Client "<CLIENT IP>", "220 Welcome to AmanIsDude's FTP Service!"
Thu Oct 28 16:47:57 2010 [pid 2] FTP command: Client "<CLIENT IP>", "USER <USERNAME>"
Thu Oct 28 16:47:57 2010 [pid 2] [<USERNAME>] FTP response: Client "<CLIENT IP>", "331 Please specify the password."
Thu Oct 28 16:47:57 2010 [pid 2] [<USERNAME>] FTP command: Client "<CLIENT IP>", "PASS <password>"
Thu Oct 28 16:47:57 2010 [pid 1] [<USERNAME>] OK LOGIN: Client "<CLIENT IP>"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "230 Login successful."
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP command: Client "<CLIENT IP>", "SYST"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "215 UNIX Type: L8"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP command: Client "<CLIENT IP>", "FEAT"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "211-Features:"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", " EPRT??"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", " EPSV??"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", " MDTM??"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", " PASV??"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", " REST STREAM??"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", " SIZE??"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", " TVFS??"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", " UTF8??"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "211 End"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP command: Client "<CLIENT IP>", "OPTS UTF8 ON"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "200 Always in UTF8 mode."
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP command: Client "<CLIENT IP>", "PWD"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "257 "/""
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP command: Client "<CLIENT IP>", "TYPE I"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "200 Switching to Binary mode."
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP command: Client "<CLIENT IP>", "PASV"
Thu Oct 28 16:47:57 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "227 Entering Passive Mode (98,248,145,79,4,1)."
Thu Oct 28 16:47:58 2010 [pid 3] [<USERNAME>] FTP command: Client "<CLIENT IP>", "LIST"
Thu Oct 28 16:48:58 2010 [pid 3] [<USERNAME>] FTP response: Client "<CLIENT IP>", "425 Failed to establish connection."
```I've replaced the username with <USERNAME> and the client's IP with <CLIENT IP ADDY>.  Again, any insight would be helpful.  Thanks all!

---

### Post by amanisdude on 2010-11-07
Thunderbump!!!

UPDATE:  Seems to me that, since passive mode works within the LAN and not the WAN, Comcast actually somehow blocks passive FTP.  Any ideas on how this might be possible?

---

