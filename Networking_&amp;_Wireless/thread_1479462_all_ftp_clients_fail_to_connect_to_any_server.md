---
title: "all ftp clients fail to connect to any server?"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by wendallsan on 2010-05-10
Hi all,

At some point my Ubuntu 9.10 install has stopped being able to connect via ftp to servers.  I have several servers that I have accounts to and I have several ftp clients installed on my system, including gftp, Filezilla, and command line ftp tools.  None of them can connect to any of my servers.  This has persisted for a while and I haven't figured out what the problem is, so it's time to start asking.

Here it is from the command line:
> ftp mywebsite.com
ftp: connect: Connection refused

I can connect fine with my netbook running Ubuntu, only my desktop has this problem, and of course I use my desktop for development.  Do I have a firewall running or something that's blocking my outgoing requests over port 21?  Any advice on how to troubleshoot this would be greatly appreciated.

---

