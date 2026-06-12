---
title: "Remote file access options"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by kaprikawn on 2009-05-17
Hi,

I've got a computer running Hardy desktop that is acting as my principle file server over my local network.

I use Samba to serve files to my Windows machines and SSH for my local Linux-based computers.

I'd like to be able to access my files over the internet.  I've set up ddclient and a dyndns account to get around my lack of static IP address.  What are my options with regards to serving my files over the internet?  I don't mind doing the research, I just need pointing in the right direction.

When I was in college I had a network drive which I could access remotely through a web browser.  I typed in the appropriate URL, then username and password and it displayed my files much like they would have been displayed in Windows Explorer if I had been on a local machine (but obviously slower to transfer/update).  Ideally this is the kind of thing I want.  It must be able to serve files to any platform, not just *nix machines.

Thanks in advance.

---

### Post by dmizer on 2009-05-17
Lots of options for you with variying levels of difficulty. If you use SSH locally, you can also use SSH from the WAN. There are tools for Windows like [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/) and [Cygwin](http://www.cygwin.com/). With either of those, you could get access to your local files via scp in Windows.

You could also set up an FTP server. The third link in my sig links to a very good FTP howto.

VPN may also be an option for you depending on how able you are in server configuration. Here's some VPN information: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

When considering a WAN accessible file server, it's critical to seriously consider security. I strongly suggest using only encrypted protocols like SSH, VPN, and SFTP/FTPS.

---

