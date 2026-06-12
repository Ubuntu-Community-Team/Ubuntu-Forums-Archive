---
title: "Remotely access a Windows network shares from XP using an ubuntu server as 'gateway'"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by koenlek on 2009-01-17
Hi everybody.

I live with 10 good friends in a student house. We have a network containing lots of stuff like movies, presentations, documents etc. Each one of us use Windows as the primary OS (I am the only one using linux too) and so our network exists out of Windows network shares. We use these network shares very much.

We would like to be able to acces these files remotely too (when being not inside the house). So I am looking for a way to make the network shares accesible remotely.
I can't find a clear way how to do this. There are two potential 'gateways' to access it: 1. An Ubuntu Server (8.04) hosting our own website. 2. A Windows XP computer in the living room that is always turned on.(these 'gateways' of course will be reached using a port forward in the router)
Of course, I would like to go for option 1. But how? Using Samba I guess, but do I need to combine it with VPN or something?
Is it a good idea to make one samba share that 'mounts' all the avialable shares (or computers) in the local network in one folder and share that folder to the 'world' using (s)ftp or something? It would be best when a normal windows pc can access this share without any extra software (just by adding a network drive in Windows Explorer). 
In other words: is it possible to share the overview you get in Gnome when clicking on "network" in the 'places' menu?

So shortly said: How do I make my windows local network shares accessible from outside the network? or: How do i connect externally to a local windows network? What is the best way to do that (using either a windows pc of ubuntu server 8.04)?

I hope my question is a bit clear. Hopefully some of you can give help me a hand so I can get this to work.

Thanks in advance, Koen

p.s. Of course I want the local network to ask for a password when the external pc wants to connect to it.
p.p.s Remote Login to a computer in a sense of 'taking over the desktop' is not what I mean. I don't want to acces the computer I just want to acces the local network shares. So VNC, MS Remote Desktop are as far as I know no option.

---

### Post by nixscripter on 2009-01-18
Allow me to offer two different answers:

1. If you set up SSH on your server, you can use sshfs to connect to it, and browse it like a normal directory on your desktop in Gnome. More info on sshfs is here: [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html) Gnome won't find it automatically, however; you have to connect manually (with a utility).

2. If you can live with a simple directory listing in a web browser (like an FTP site), then you can use the [null httpd daemon]("http://nullwebmail.sourceforge.net/httpd/") for that; but I don't think it supports secure authentication.

3. If you want to have windows PCs able to connect to it, make it an SMB server. I'm afraid I know very little about that.

Hopefully one of these is what you want.

---

