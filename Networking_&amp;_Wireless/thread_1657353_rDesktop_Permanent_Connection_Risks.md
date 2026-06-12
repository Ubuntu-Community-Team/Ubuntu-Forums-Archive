---
title: "rDesktop Permanent Connection Risks?"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by Sugi on 2011-01-01
I have successfully setup a connection from Ubuntu 10.10 to Windows XP Pro via rDesktop, which of course was quite easy, but I intend to do permanently setup via my computers on the same connection. Like KVM switch, but what kind of risks or problems could come up?  What kind of tweaks could I apply to add extra security?  

I would like to do a ssh connection between them, but I have had major issues with it in the past.  What kind of options do I have?

Updated Links:
OpenSSL vulnerability: [http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1)
rDesktop Windows XP: [http://pricklytech.wordpress.com/2010/04/29/ubuntu-10-4-lucid-remote-desktop-to-windows-xp-professional/](http://pricklytech.wordpress.com/2010/04/29/ubuntu-10-4-lucid-remote-desktop-to-windows-xp-professional/)
bitvise: [http://www.bitvise.com/wug-connecting](http://www.bitvise.com/wug-connecting)
TightVNC: [http://members.shaw.ca/nicholas.fong/vnc/](http://members.shaw.ca/nicholas.fong/vnc/)
Setup: [http://www.rasyid.net/2007/05/18/install-ssh-server-in-windows-xp/](http://www.rasyid.net/2007/05/18/install-ssh-server-in-windows-xp/)
TightVNC Page: [http://www.tightvnc.com/winst.php](http://www.tightvnc.com/winst.php)


Thanks for reading,
Sugi

---

### Post by PatchesTheCaveman on 2011-01-01
Micrpsoft didn't add support for Transport Layer Security (TLS) on their Remote Desktop Protocol (RDP) until Windows Server 2003.  Windows Vista was the first client version of Windows with TLS.  While earlier versions did support a proprietary encryption method, it is vulnerable to a man-in-the-middle attack:  [http://www.securiteam.com/windowsntfocus/5EP010KG0G.html](http://www.securiteam.com/windowsntfocus/5EP010KG0G.html)

Consider upgrading to a newer version of Windows or tunneling through SSH if you are worried about tampering or monitoring on your local network. As long as the computers are firewalled such that there is no RDP access from outside the local network you shouldn't have to worry about outside attacks, though.

---

### Post by PatchesTheCaveman on 2011-01-01
Micrsoft didn't add support for Transport Layer Security (TLS) on their Remote Desktop Protocol (RDP) until Windows Server 2003.  Windows Vista was the first client version of Windows with TLS.  While earlier versions did support a proprietary encryption method, it is vulnerable to a man-in-the-middle attack:  [http://www.securiteam.com/windowsntfocus/5EP010KG0G.html](http://www.securiteam.com/windowsntfocus/5EP010KG0G.html)

Consider upgrading to a newer version of Windows or tunneling through SSH if you are worried about tampering or monitoring on your local network.  
As long as the computers are firewalled such that there is no RDP access from outside the local network you shouldn't have to worry about outside attacks, though.

---

### Post by Sugi on 2011-01-01
I am currently trying TightVNC within Windows XP [I believe ssh would be the best option for remote access], and looking for a good tutorial on setting it up for my ubuntu to view the server.  Have any reference for doing this?  I keep getting connection timed out on viewer.

Sugi

---

### Post by PatchesTheCaveman on 2011-01-01
VNC also requires a SSH tunnel for security.  I would recommend sticking with RDP because it provides better graphical performance than TightVNC.

To secure your connection over an SSH tunnel, you have two options:
There is a commercial solution for SSH on Windows that works well and is free for personal use:  [http://www.bitvise.com/winsshd](http://www.bitvise.com/winsshd)

You can also use OpenSSH on the Cygwin POSIX compatibility layer:  [http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

---

### Post by Sugi on 2011-01-01
Thank you very much for the links, I will report back with my findings and experience with these applications.  I am currently testing them in a virtual operating system.

Sugi

---

