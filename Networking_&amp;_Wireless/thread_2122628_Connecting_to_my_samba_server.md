---
title: "Connecting to my samba server"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by amarek on 2013-03-05
So I have a samba server setup running on Ubuntu server 12.04. I can connect to it anywhere over the home network. Now I've setup port forwarding and it's on the default port 445. I can connect to it via the router's IP but still only when I'm on the same network. I tried setting up an Apache server on the same computer and router and I can can access the web page from any other network. Help please, am I missing something? a samba config maybe?

---

### Post by bab1 on 2013-03-05
> **amarek said:**
> So I have a samba server setup running on Ubuntu server 12.04. I can connect to it anywhere over the home network. Now I've setup port forwarding and it's on the default port 445. I can connect to it via the router's IP but still only when I'm on the same network. I tried setting up an Apache server on the same computer and router and I can can access the web page from any other network. Help please, am I missing something? a samba config maybe?

Samba protocols are generally not permitted over the Internet.  You need to use a VPN to access Samba outside of your own LAN.

---

### Post by amarek on 2013-03-08
> **bab1 said:**
> Samba protocols are generally not permitted over the Internet.  You need to use a VPN to access Samba outside of your own LAN.
Okay, thank you for your help. Now since I really don't want to use a VPN is there another type of file server you could suggest?

---

### Post by garcianc2003 on 2013-03-11
You could try to setup a SSH server. There are clients for Windows (i.e. Swish, WinSCP) that will allow easy file access with drag-and-drop functionality.

---

### Post by prodigy_ on 2013-03-11
> **bab1 said:**
> Samba protocols are generally not permitted over the Internet.
Not exactly. :) There's nothing about the SMB protocol that would prevent it from working over the Internet. Some providers block default ports utilized by SMB (such as 445) but you can work around that - e.g. by forwarding different ports from your router.

Still, I agree that SSH/SFTP is a much better idea. You can also use SSH to forward samba ports over a secure tunnel:
[http://simonholywell.com/post/2009/04/samba-file-share-over-ssh-tunnel.html](http://simonholywell.com/post/2009/04/samba-file-share-over-ssh-tunnel.html)

---

### Post by bab1 on 2013-03-11
> **prodigy_ said:**
> Not exactly. :) There's nothing about the SMB protocol that would prevent it from working over the Internet. Some providers block default ports utilized by SMB (such as 445) but you can work around that - e.g. by forwarding different ports from your router.

Still, I agree that SSH/SFTP is a much better idea. You can also use SSH to forward samba ports over a secure tunnel:
[http://simonholywell.com/post/2009/04/samba-file-share-over-ssh-tunnel.html](http://simonholywell.com/post/2009/04/samba-file-share-over-ssh-tunnel.html)
Browsing for shares is the only reason to use Samba.  You can't do that easily over the Internet without resorting to using a VPN.  As you say it's easier to just use SSH/SFTP.

---

