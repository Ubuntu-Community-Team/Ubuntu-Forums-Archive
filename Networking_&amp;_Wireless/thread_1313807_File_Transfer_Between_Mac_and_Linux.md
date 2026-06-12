---
title: "File Transfer Between Mac and Linux?"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by lariosa42 on 2009-11-04
I have about 40GB of music I want to transfer from my Linux machine to a Mac.  I would like to do it without having to put 1GB at a time on my flash drive.  I figure I should be able to transfer through ethernet cables, possible using my router.

I am writing because I'm pretty ignorant about networking, and don't even know what to google for.  Can anyone point me in the right direction, or at least tell me if it is possible?

---

### Post by sedawk on 2009-11-04
If both systems are connected to the router the router
should provide IP addresses for both of them (DHCP).

First you have to know these addresses: try
"ifconfig" or "ifconfig eth0" on the command line.

Now there are many ways to continue:

* Run a web server on Linux and browse your music from the Mac
* Run samba to create a shared drive that the Mac can see

But what I recommend:

* install sshd on Linux (package should be openssh-server)
  then then you can use ssh/scp/sftp/rsync_via_ssh from the
  Mac to transfer  the files from the linux box.
  This is the easiest to set up (but not the easiest to use).
  Check which tools are already part of your mac installation.

---

### Post by Iowan on 2009-11-04
[Here]("http://ubuntuforums.org/showthread.php?t=218630") is an FTP option for you.

---

### Post by lespaul_rentals on 2009-11-04
> **sedawk said:**
> If both systems are connected to the router the router
should provide IP addresses for both of them (DHCP).

First you have to know these addresses: try
"ifconfig" or "ifconfig eth0" on the command line.

Now there are many ways to continue:

* Run a web server on Linux and browse your music from the Mac
* Run samba to create a shared drive that the Mac can see

But what I recommend:

* install sshd on Linux (package should be openssh-server)
  then then you can use ssh/scp/sftp/rsync_via_ssh from the
  Mac to transfer  the files from the linux box.
  This is the easiest to set up (but not the easiest to use).
  Check which tools are already part of your mac installation.

Why use SFTP?  As much as I love SSH, the transfer speeds are less than ideal.

I would recommend using vsftpd.  Download using your preferred method of installing packages.  It's in the repositories.

It creates a config file in /etc/vsftpd.conf.  This file is well-commented and should be easy to edit.  If you need help, feel free to get back to me and I will explain.

This will create an FTP server on your Ubuntu machine that you can use to transfer files.

---

### Post by Lars Noodén on 2009-11-05
> **lariosa42 said:**
> I have about 40GB of music I want to transfer from my Linux machine to a Mac.  I would like to do it without having to put 1GB at a time on my flash drive.  I figure I should be able to transfer through ethernet cables, possible using my router.

I am writing because I'm pretty ignorant about networking, and don't even know what to google for.  Can anyone point me in the right direction, or at least tell me if it is possible?

I would second @ sedawk 's three suggestions.  The recommendation could include sshfs.  

If it's just music and you would like to try streaming it instead, then you can look at vlc or icecast.

---

### Post by KingBongo on 2009-11-10
Hi. I managed to connect via SSH from OS X to Ubuntu and vice versa. I have one question though. When connecting to the Mac (via Network - SSH) all files are graphically displayed, even those that are normally hidden in OS X. Can that be avoided? How?

PS. Speed is acceptable for me.

---

