---
title: "best way to push files across networked computers?"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by gforster on 2009-08-26
I have a small lab of 30 computers at our school all running ubuntu 9.04. If I want them all to have a folder with some practice documents and files, what is the best way to make sure each computer has a copy of those files? Would it be using scp or another command-line utiltiy?  Or is there a gui way to do this for non-techie teachers that want their students to have certain files?

---

### Post by fela on 2009-08-26
Have one computer with the files on it, and share the right folder via NFS to the other computers. If you need instructions on that I'll gladly tell you.

---

### Post by zman58 on 2009-08-26
There are many ways to do this...

I would recommend providing a share on the server (main computer) and let each of the workstation users connect to that share to copy and paste the folder into their system (such as on their desktop). There are of course other options...
...They could connect to the server using the taskbar
"Places - Connect to Server"
select "Windows Share" and provide the necessary share name and credentials and voila, they would have a connection to the server pointing at the fileshare directory that was set up.
--or they could browse to the server from the desktop using Places - Network.
--or you could provide them a neat little script to run that mounts the server share and copies the latest set of files from the server to the local computer in a writable location somewhere below ~/ (home).
--or you could set up a cron job on each of the workstations to automatically mount and copy the latest files from the server at a specific time of the day or night.
--or you could set up the workstations to have a permanent mountpoint in the filesystem set to the server share that allows them to see a read-only set of files which are actually on the server. They would have to copy then paste them locally if they wanted to edit or change them. ...Very easy to do.

The credentials are established when you set up the samba share on the server. You could make it broadly accessible with simple password or no password or provide an account (name and password) for each of the machines to attach with.

Samba is a CIFS or windows style network sharing program. I use it on my server at home. It is incredible. It works flawlessly. It is available in the ubuntu repositories and can easily be added to your system using the installer or Synaptic package manager.

I use samba for this purpose on the server for our home network. You can read about my home server here. I use samba and have a config file that you can use if you want to. I also have mounting scripts if you want to automate some of the file management. Download the config files and pull whatever you need from them such as the samba config file. What I have there works perfectly in our network--all scripts and config files. It has all been tested and is the latest that I have. There is a readme file also to bring you up to speed with how I am using the parts.
[http://home.roadrunner.com/~zahorec/gatekeeper.html](http://home.roadrunner.com/~zahorec/gatekeeper.html)

So first read up just a little on samba and the samba config file smb.conf. Samba is what makes the files available on the server so the workstations can get to them. Lots of documentation on the web of course. There are also some very good books on samba. You can even find samba help on youtube!

---

### Post by fela on 2009-08-26
@zman58: for *nix servers to *nix clients, NFS beats samba. By a wide margin.

So I advise you to use NFS.

I don't know how lucky you are with your server setup, but on my ubuntu server samba was a right PITA to setup. NFS worked flawlessly on first go, with absolutely no experience using NFS before. It took me no more than 5 minutes (at very most) to setup all my NFS shares on my home server.

---

### Post by zman58 on 2009-08-27
> **fela said:**
> @zman58: for *nix servers to *nix clients, NFS beats samba. By a wide margin.

So I advise you to use NFS.

I don't know how lucky you are with your server setup, but on my ubuntu server samba was a right PITA to setup. NFS worked flawlessly on first go, with absolutely no experience using NFS before. It took me no more than 5 minutes (at very most) to setup all my NFS shares on my home server.

One reason I typically use samba for our server shares is that every now and then we get a Windows laptop connected to the network and I want them to be able to easily access the server shares. It doesn't take more than a few minutes to set up a simple samba share--once you have done it a couple of times anyway.

I have not tried to get Windows to attach to a NFS share--can you do that with typical Windows system or do you have to add a file system driver for NFS?

I actually have not tried to use NFS before with a Linux server, but have heard that it is very fast and reliable. Glad to hear it is easy and I will research it to learn more. ...So as you point out, it is also a very good option. Thanks for the advice.

---

### Post by fela on 2009-08-27
> **zman58 said:**
> One reason I typically use samba for our server shares is that every now and then we get a Windows laptop connected to the network and I want them to be able to easily access the server shares. It doesn't take more than a few minutes to set up a simple samba share--once you have done it a couple of times anyway.

I have not tried to get Windows to attach to a NFS share--can you do that with typical Windows system or do you have to add a file system driver for NFS?

I actually have not tried to use NFS before with a Linux server, but have heard that it is very fast and reliable. Glad to hear it is easy and I will research it to learn more. ...So as you point out, it is also a very good option. Thanks for the advice.

Yes, definitely try NFS if you're only using *nix.

As for samba, the first time I set it up I had to logout and then in again on my server, while it was doing something useful.

It took me 10 minutes to setup the first share, 5 minutes the next ones. Too long if you ask me. I can literally do all the NFS stuff in less than 1 minute now.

EDIT: of course that's not the reason I don't use Samba!

---

### Post by i.r.id10t on 2009-08-27
You could make a .deb package with the files and create your own repository.  Then when you need to make changes, replace/update the deb file in the repo and let apt get the new versions.

---

### Post by junglist313 on 2009-08-27
If they are all sharing the same wireless connection but not formally "networked" I would recommend Giver. Here is a link: 

[http://code.google.com/p/giver/]("http://code.google.com/p/giver/")

---

### Post by gforster on 2009-08-30
Wow so many options and ways I never considered. I will toy around with some of the ideas mentioned here.

---

