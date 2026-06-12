---
title: "Whats the best way to seamlessly access my Ubuntu server's HDD in OS X's Finder?"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by jamieh on 2009-01-15
Hey,
I didn't know weather to post this here or on MacRumors, but I have an Ubuntu server I use to store assorted files. I have been using Cyberduck on OS X to access the server via SFTP, but I'd prefer to  have seamless integration with the Finder. Can this be done?

I tried using a trial of "ExpanDrive" but it's REALLY buggy.

Going to "Connect To Server..." in OS X's menu bar lets me connect to the following protocols:

- Mac computers that have file sharing turned on
- Windows computers with shared folders
- AirPort disks
- AFP servers
- SMB/CIFS or NFS servers
- FTP servers **(read-only)** [COLOR="Red"](Screw that)[/COLOR]
- WebDAV servers[COLOR="red"] (You need to spend hours screwing around with Apache to get this to work, yes?)[/COLOR]

Can someone help me decide on the best method to access the server?
I'd like to be able to access it worldwide like I do with Cyberduck. From my understanding, AFP is LAN-only.

Thanks

---

### Post by blackened on 2009-01-15
Have you tried openssh-server on the server and sshfs on the client? I don't know how good the mac version of sshfs is, but this setup works perfectly in a Linux->Linux environment.

---

