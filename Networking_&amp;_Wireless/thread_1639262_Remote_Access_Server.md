---
title: "Remote Access Server"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by mristok on 2010-12-06
I have been interested in deploying an ubuntu server for some time now. But I need to be able to access computers on the network remotely, not remote connection to the server itself. Can ubuntu (as is) support as a remote access server to windows machines on the network? Is there a third party developer that supports this function? 
 
Also, I have and FTP server offsite, and am wondering the best and fastest file transfer way to keep the two synced.
 
Thanks ahead of time!

---

### Post by DaithiF on 2010-12-08
well theres a variety of ways to connect to a windows PC from a linux box -- rdesktop supports the windows terminal server protocol, so it would be equivalent to using mstsc.exe to connect from one windows machine to another, if thats what you're familiar with.

Theres also VNC, where you would put a small vnc server on the target PCs, and a client on the linux box.

the one slight issue is that both of these will require a graphical environment on the linux machine, and thats a little unusual for a linux server (unlike windows servers, linux servers don't typically have a graphical environment installed).  Theres no particular problem installing a gnome or kde desktop on the server, i point it out just so you're aware that you won't get one with a typical server distro install 'out-of-the-box'

---

### Post by Sub101 on 2010-12-08
> **mristok said:**
> I have been interested in deploying an ubuntu server for some time now. But I need to be able to access computers on the network remotely, not remote connection to the server itself. Can ubuntu (as is) support as a remote access server to windows machines on the network? Is there a third party developer that supports this function? 
 
Also, I have and FTP server offsite, and am wondering the best and fastest file transfer way to keep the two synced.
 
Thanks ahead of time!

To my knowledge you would need either a VNC server or SSH server installed on each of the networked PCs you want to access.

---

### Post by dmizer on 2010-12-09
> **mristok said:**
> But I need to be able to access computers on the network remotely, not remote connection to the server itself. Can ubuntu (as is) support as a remote access server to windows machines on the network?

It sounds as though what you need is two things. First, you'll need a VPN server. You'll also need to install remote desktop servers on the Windows machines.

A VPN server will allow your remote PC to securely (over an encrypted channel) become part of your LAN, just as though your remote PC was directly plugged into the same router as all the rest of your machines. Since your remote machine then becomes part of the network, you can use any remote desktop application to access the Windows computers. More on VPN here: [http://en.wikipedia.org/wiki/Virtual_private_network](http://en.wikipedia.org/wiki/Virtual_private_network)

Here's a good howto for creating an Ubuntu based VPN server: [https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

The second part of this puzzle is remote desktop. In order to get direct access to the Windows machines, you will need to install remote desktop servers on each of the Windows machines. A good server to use for remote desktop is called TightVNC. TightVNC works on both Windows and Linux based computers. You can find TightVNC here: [http://www.tightvnc.com/](http://www.tightvnc.com/)

I know of no other way to accomplish what you want to do.

---

### Post by pricetech on 2010-12-10
If I read your post correctly, I've done exactly what you're trying to do, with great success.

Start with the desktop version.  You can add what servers you need to it rather than adding a desktop environment to the server version.  It can be done either way, but since you're new to Linux, I recommend adding servers to the desktop.  I also recommend you use 10.04 Lucid Lynx since it's a Long Term Support release.

Anyway.

Once you have Ubuntu installed and updated, install the following: (you can search for these in Synaptic exactly the way they are typed here)
fail2ban
openssh server
system-config-samba
vsftpd
xvnc4viewer

Once these are done, download and install NX from nomachine.com You'll want the Client, Node, Server for Linux and if you think you might need it, download the Client for Windows.

Back up some files that will be edited, either directly or indirectly:
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config_orig
sudo cp /etc/ssh/ssh_config /etc/ssh/ssh_config_orig
sudo cp /usr/NX/etc/node.cfg /usr/NX/etc/node.cfg.orig
sudo cp /usr/NX/etc/server.cfg /usr/NX/etc/server.cfg.orig
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.orig
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.orig

You won't need to edit sshd_conf or ssh_conf just yet, though you may want to later.  Just leave them be for now.

Edit your node.cfg and server.cfg files and search for "22".  Make sure the lines that contain that number don't have a hash (#) in front of them. I saw that with my most recent install of NX.
You'll find it once in node.cfg
SSHDPort = "22"
and twice in server.cfg
SSHDPort = "22"
and
SSHDAuthPort = "22"
I like to edit with nano like this:
sudo nano /usr/NX/etc/node.cfg
and
sudo nano /usr/NX/etc/server.cfg

Once the computer is restarted, you should be able to connect using any SSH client and / or with NX client.

Once you're connected to your Ubuntu box, use Terminal Server Client to connect to your Windows boxen.  The addition of xvnc4server makes TSClient support VNC (Tight VNC) on your Windows boxen if you prefer, or need, to connect that way.

That's enough to get you started.

Read more as you can and migrate your way to a more secure SSH by using keys rather than passwords.

Read the server guide on the website for details about making FTP work (it's actually simple, I just don't have the steps handy.

Samba is for sharing files with your Windows boxen, which you'll probably want to do eventually if not right away.  Just use System - Administration - Samba to configure it.  No manual editing of smb.conf is necessary.

Post back with additional questions and someone will try to help you.

P.S. If I've misunderstood your post, I just wasted several minutes typing all this, but that's okay.  Maybe someone else can use it.

Joe

---

