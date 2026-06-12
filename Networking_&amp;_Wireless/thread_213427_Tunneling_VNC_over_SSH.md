---
title: "Tunneling VNC over SSH"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by zugu on 2006-07-11
Hello,

I am in the following situation: my home PC is directly connected to the Internet and it's running Ubuntu. My work PC is behind a router and is running Windows XP.

As far as I understand, I can get a remote desktop from my workplace only by using a Windows VNC client over a SSH connection.

I activated remote desktop and installed openssh-server on the Ubuntu machine, set up a password, and installed putty and a VNC client on the Windows machine.

Now what do I do in order to get the tunnel working?

I am also interested in similarily tunneling FTP over SSH (a.k.a. SCP).

Cheers.

---

### Post by Paerez on 2006-07-11
here is how to forward a port using putty:
[http://www.cs.uu.nl/technical/services/ssh/putty/puttyfw.html](http://www.cs.uu.nl/technical/services/ssh/putty/puttyfw.html)

follow this guide using the port vnc uses (or ftp). I think vnc uses 5900 by default, and I know ftp is 21.

You have to log in with putty with these settings, and as long as you are logged in, putty maps the port on your server to yourself, letting you connect to putty, which connects you to your server. Its sweet.

---

### Post by zugu on 2006-07-11
Thank you. Any suggestions concerning SCP?

---

### Post by Paerez on 2006-07-11
use WinSCP. SCP goes over the ssh ports I think so no extra work is necessary.

---

### Post by abowman on 2006-07-16
This is how I do it:
[Secure Remote Access with VNC and SSH]("http://abowman.com/2006/07/02/secure-remote-access-with-vnc-and-ssh/")

---

### Post by inthewayboy on 2006-07-18
Once you have OpenSSH installed you have two main ways of transfering files...SCP and SFTP. From what I know (And it's not a lot) SCP is from SSH1 and SFTP is from SSH2. So go with SFTP if you can, as you'll benefit from all the new stuff. I can't comment on what is better, but I know it's worth it.

However, the SFTP functions will probably only operate on the SSH host, and not another computer in the network. I may be wrong on that. If you need access to files on a server past the SSH host you could tunnel port 21 to a standard FTP server and at least gain the encryption benefits. 

As far as an SFTP client you can stick with WinSCP or you can use the excellent FileZilla.

---

