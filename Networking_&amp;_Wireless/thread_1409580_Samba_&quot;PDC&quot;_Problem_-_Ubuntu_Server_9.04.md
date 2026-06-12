---
title: "Samba &quot;PDC&quot; Problem - Ubuntu Server 9.04"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by Overcast32 on 2010-02-17
I'm attempting to make a Samba Domain Controller on my home network - so no existing Windows Servers at all.. 

Followed this: [https://help.ubuntu.com/9.04/serverguide/C/samba-dc.html]("https://help.ubuntu.com/9.04/serverguide/C/samba-dc.html")

Everything seems (well almost everything) to be working ok - I can see the 'netlogon' share and when I attempt to join the domain with WinXP 32-bit, it prompts me for a username/password but when I try to join it fails: "The specified domain either does not exist or could not be contacted."

I tried an intentionally incorrect domain name and it returns "a domain controller cannot be contacted" - that's expected as it can't find that fake domain at all naturally, so it seems to be responding to the attempts to join the domain otherwise.

In another attempt at this, I intentionally used a bad username and password and it fails with the first error again - so I'm thinking it may be some sort of permissions issue for that account. (I've tried the user name as *'username'* and also as *'DOMAIN/username'* as well, not sure which it wants). But do want to note, with the same username/password I can map drives from the Windows machine to the Ubuntu machine just fine, otherwise - it accepts that username/password without any 'domainname' etc.. 

*I did a packet capture and the one notable packet I do see is a "SAM Response - user unknown" - but I can't figure out why it will take the user/pass to map a drive, but not to join the domain.*

It's a default Ubuntu Server 9.04 install - No GUI loaded all CLI at this point. Other than SSH Server and DNS/BIND nothing's been added at all.. 

Any ideas?

I did create a 'machines' group like noted in the Ubuntu Doc link above. 

The only account that exists on the Ubuntu/Samba server now is the default one created during installation. 


I'm still digging around, but thought I would post a question, just in case someone ran into this or has a good idea of what it is.. :)

Edit: oh and.. on this part.. 

*"With root being disabled by default, in order to join a workstation to the domain, a system group needs to be mapped to the Windows Domain Admins group. Using the net utility, from a terminal enter:"*

I mapped it as such (since there was no 'sysadmin' group - that I know of.. 

```
sudo net groupmap add ntgroup="Domain Admins" **unixgroup=adm** rid=512 type=d
```

Is that my goof?

---

### Post by oneindelijk on 2010-02-17
Hi, have you tried using <domain>.local for joining the XP machine ?

---

### Post by Overcast32 on 2010-02-17
> **oneindelijk said:**
> Hi, have you tried using <domain>.local for joining the XP machine ?

You mean in the Windows 'computer name' dialogue?

I just did and it acts like it can't find a DC:
[I]
The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)[/I]

---

### Post by oneindelijk on 2010-02-17
Yes, that's what I mean.
Does it make any difference ?
Have you checked the logfiles on the server when the XP machine attempts to join the domain ?

---

### Post by Overcast32 on 2010-02-17
> **oneindelijk said:**
> Yes, that's what I mean.
Does it make any difference ?
Have you checked the logfiles on the server when the XP machine attempts to join the domain ?

It just acts like it can't find a DC at all then. 

As for the logs - under /var/samba - there's a few things in there, but I can't seem to match the timestamps in the logs with anything going on.. (I last tried to join @ 20:29 - no events right at that time that I can tell.. but then, I'm a rank n00b at this.. :)

But it does seem to point to something.. 

```
[2010/02/17 19:32:49,  0] lib/util_sock.c:write_data(1136)
[2010/02/17 19:32:49,  0] lib/util_sock.c:get_peer_addr_internal(1676)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2010/02/17 19:32:49,  0] smbd/process.c:srv_send_smb(74)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2010/02/17 19:32:54,  0] smbd/service.c:make_connection_snum(744)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/02/17 19:32:55,  0] smbd/service.c:make_connection_snum(744)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/02/17 19:33:03,  1] smbd/service.c:make_connection_snum(1115)
  orion (192.168.0.5) connect to service var initially as user *username* (uid=1000, gid=1000) (pid 2970)

```

And this from: log.winbindd-idmap


```
[2010/02/17 20:26:11,  1] winbindd/idmap_tdb.c:idmap_tdb_alloc_init(341)
  idmap uid or idmap gid missing
[2010/02/17 20:26:11,  0] winbindd/idmap.c:idmap_alloc_init(587)
  ERROR: Initialization failed for alloc backend, deferred!
```

---

### Post by Overcast32 on 2010-02-17
Also curious - [_in this thread_]("http://ubuntuforums.org/showthread.php?t=1314386"), it mentions DNS setup.. 



Does DNS need to be fully setup for this to work? (believe it's using winbind though.. )

---

### Post by Overcast32 on 2010-02-17
Think I'll give this guide a shot, will update thread with results.. 

[http://ubuntuforums.org/showthread.php?t=1184288]("http://ubuntuforums.org/showthread.php?t=1184288")

---

### Post by Overcast32 on 2010-02-18
Got it working perfectly :)

[http://ubuntuforums.org/showthread.php?t=1330637]("http://ubuntuforums.org/showthread.php?t=1330637")

And the above thread - were fantastic!

---

