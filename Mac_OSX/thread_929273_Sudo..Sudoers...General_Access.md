---
title: "Sudo..Sudoers...General Access"
date: 2008-09-24
forum: Mac OSX
---

### Post by dfnkt on 2008-09-24
I am using Altiris Deployment Server that runs a job on some Mac computers that we have. The job is very simple and is comprised of two parts.

Job: Deploy the Altiris NS Agent for Mac
Task1: Copy file to
Details: Copy from \\server\share1\aex-bootstrap.Z to / (root on Mac HD)

Task2: Run Script
Details: 
cd / (changes to root)
uncompress aex-bootstrap.Z && chmod u+x aex-bootstrap && sudo ./aex-bootstrap [http://altiris_server.acme.com](http://altiris_server.acme.com)

The run script basically is doing a change dir to the root (where the file was copied in task1). Then it has a set of commands chained together.

The uncompress command works perfectly, the aex-bootstrap.Z file becomes uncompress as aex-bootstrap on the root. The change mod to executable command is also functioning as intended. The problem happens when the sudo command is used to assume super user status to execute aex-bootstrap from the current dir and set the location of the Altiris Notification Server.

Question is this: How do you solve this problem? It wouldn't be smart to pass the password in the script (if it's even possible) but I wonder if it is the only possible solution. I thought about editing the list of sudoers but I do not wish to attempt this as I would need to repeat this task on 300 computers.

Ideas?!:confused:

---

### Post by Sef on 2008-09-24
Are you running this script on a Mac computer with what os: OSX or Ubuntu?

---

### Post by dfnkt on 2008-09-24
Yes the script is executed on MAC OS X (10.4.11), While it is mac, in the terminal it's still unix

---

### Post by bab1 on 2008-09-25
You can use SUID for this.  See:
[http://www.gnufans.net/~deego/pub/DeegoWiki/DebianSetuid.html]("http://www.gnufans.net/~deego/pub/DeegoWiki/DebianSetuid.html")
[http://sisc.sdsu.edu/doc/debian/ch-advanced.html]("http://sisc.sdsu.edu/doc/debian/ch-advanced.html")

Read the pertinent parts on the sticky bit attribute.  This may need to be confirmed for OSX as it uses BSD as it's base.

Essentially you need to set the perms on the script to be something like: 4770 and owned by [COLOR="Blue"]root[/COLOR] and the group being [COLOR="Blue"]someadmingroup[/COLOR].  This will allow you to run the script as root while you are a member of the [COLOR="Blue"]someadmingroup[/COLOR] group.

This has nothing to do with sudo.  It can be a security risk.  But if used wisely it has its place.

---

### Post by Sef on 2008-09-25
> Yes the script is executed on MAC OS X (10.4.11),  While it is mac, in the terminal it's still unix 	

Moved to BSD Discussions.   General Help is restricted to Ubuntu, Kubuntu, and Xubuntu.  Also OSX is directly based, in part, on FreeBSD.

---

### Post by cardinals_fan on 2008-09-25
> **Sef said:**
> Moved to BSD Discussions.   General Help is restricted to Ubuntu, Kubuntu, and Xubuntu.  Also OSX is directly based, in part, on FreeBSD.
What?  We have a Mac OSX subforum that is a much better place for OS X related topics ;)

---

### Post by Bachstelze on 2008-09-26
> **cardinals_fan said:**
> What?  We have a Mac OSX subforum that is a much better place for OS X related topics ;)

Aye.

---

