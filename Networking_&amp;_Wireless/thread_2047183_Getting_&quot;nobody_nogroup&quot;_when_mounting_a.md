---
title: "Getting &quot;nobody nogroup&quot; when mounting an nfs share from ubuntu 12.04"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by pintle on 2012-08-24
Server 1 is Xubuntu (Mythbuntu) 12.04
Server 2 is Debian squeeze
Client is Debian squeeze

Applicable line from /etc/exports on server 1 is 

/video/   192.168.1.0/24(rw,insecure,async,all_squash,anongid=1000,anonuid=1000)

Applicable line from /etc/exports on server 2 is

/media/usb_1/ 192.168.1.0/24(rw,insecure,async,all_squash,anongid=1000,anonuid=1000)

The same, in other words.

When I mount the share from server 2 on the client, I see

$ ls -Alh
total 20K
drwx------ 2 doc doc 4.0K Aug 23 08:06 1_watch
drwxr-xr-x 2 doc doc 4.0K Aug 23 19:01 2_temp

where doc is the correct username and group.

When I mount the share from server 1, I see

# ls -Alh
total 36K
drwxr-xr-x  7 nobody nogroup 4.0K Jul  3  2011 artwork
drwx------  2 nobody nogroup  16K Jul  3  2011 lost+found

I have added 

NEED_IDMAPD=yes

to /etc/default/nfs-common on both client and server 1. (Before I did that I was getting 4294967294 for the user and group.)

Any ideas on how to fix this?

Any help is appreciated.

---

