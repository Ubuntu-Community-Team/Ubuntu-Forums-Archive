---
title: "Samba: server-name recognized by Nautilus, not by mount.smbfs"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by sanderj on 2009-07-19
Hi, a strange thing with Samba:

Nautilus does see my samba-server 'hdx1000' on the LAN, and can connect to it. The command 'nmblookup hdx1000' can also resolve to the correct IP address of that server. So far so good.

However, mount.smbfs does not recognize //hdx1000/share. Error message is:
>    mount error: could not resolve address for hdx1000: Name or service not known
   No ip address specified and hostname not found


Strangely enough, mount.smbfs works OK when using the IP-address (//192.168.2.146/share) and the Rendezvous/Zeroconf name (//macintosh.local./share). FYI: no, the server is not a Mac, just an embedded system running Linux.

What's going on? How can I solve this?

```

ubuntu@ubuntu:~$ nmblookup hdx1000
querying hdx1000 on 192.168.2.255
192.168.2.146 hdx1000<00>
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo mount.smbfs //hdx1000/share /mnt/hdx1000-share/ -o username=nmt,password=1234
mount error: could not resolve address for hdx1000: Name or service not known
No ip address specified and hostname not found

ubuntu@ubuntu:~$ sudo mount.smbfs //macintosh.local./share /mnt/hdx1000-share/ -o username=nmt,password=1234
ubuntu@ubuntu:~$


ubuntu@ubuntu:~$ sudo mount.smbfs //192.168.2.146/share /mnt/hdx1000-share/ -o username=nmt
Password:
ubuntu@ubuntu:~$



```

---

