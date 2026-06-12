---
title: "Unable to open OO via SSH"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by malel on 2009-03-13
I am using SSH to share files on my Desktop computer with my laptop via a wired router. All is well except for Open Office files. When I go to open a file a window pops up and asks for a password. The only password I have is for opening the computer but when I put that in it does nothing and I can't read the document file. Is there some sort of setting up required with OO?


Thank you






Desktop: Pentium 4, 3.0, 2Gb ram, 40Gb HDD
Laptop:  Acer Travelmate 240, 2.66. 1Gb ram, 40Gb HDD

---

### Post by malel on 2009-03-13
Sorry folks forgot to add the both Desktop and Laptop are running Ubuntu 8.10 fully updated

---

### Post by MaxIBoy on 2009-03-13
Are you forwarding X over SSH?
The command is
```
ssh -X user@host
```The X has to be UPPERCASE, otherwise it won't work. Also, unless you've [set up multiple X servers](https://answers.launchpad.net/ubuntu/+question/4043), the machine you're controlling remotely cannot already be running an X server (you have to kill X  first.)

Once you do that, you can then type "oowriter file.odt," "oocalc file.ods," "ooimpress file.odp," etc. When you take control of a remote machine in order to do this, openoffice has to be installed on the remote machine, but it doesn't have to be installed on the machine you're physically using.


For me, I actually run xfce4-panel over the SSH connection, and I put some shortcuts on that, so I have a more-usable connection to the server.

---

