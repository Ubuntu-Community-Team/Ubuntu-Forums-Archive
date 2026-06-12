---
title: "Migrating to a laptop"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by bomanizer on 2006-02-03
Hi, 

I'm wondering, is there a quick way to copy my files from my desktop computer to my laptop using ethernet and the onboard cards on the two computers? Can this be done with ftp in some painless manner?

I'm selling my desktop computer and I want to copy my music, etc. before the new owner takes it away.

I have some experience using ftp clients, like gFTP....

Thanks in advance!

------
Breezy + Asus with integrated network card

---

### Post by davinci on 2006-02-03
Assuming that you have a working network connection:

You could install ssh on the Desktop and use scp on your laptop to copy files/directories. 

Example:

scp -r your.desktop.ip:/home/user/ .

---

### Post by bomanizer on 2006-02-03
[QUOTE=davinci]Assuming that you have a working network connection:

You could install ssh on the Desktop and use scp on your laptop to copy files/directories. 

Example:

scp -r your.desktop.ip:/home/user/ .[/QUOTE]

Sounds good, thanks. I think I get the basic idea. What I lack is the practical know-how :cry:  A step-by-step HOWTO would be superb! :-D

---

### Post by davinci on 2006-02-03
OK, I'll try


1) Install the ssh package on the desktop: 
> sudo apt-get install ssh
   (Now you can login from your laptop to the desktop with "ssh -l yourusername your.desktop.IP"; not needed, just for illustration)

2)On your laptop use the scp command to transfer the files: > scp [email]yourusername@your.desktop.IP[/email]:/home/usr/* /laptop/directory

The scp command works just the same as the cp command:just add your username and IP before the directory

for detailed infos on the command: > man scp

---

### Post by bomanizer on 2006-02-04
Ok, let me see if I get this right...
1. Desktop with default (breezy) network configuration and DHCP
2. Laptop with default (breezy) network configuration and DHCP
3. I connect the network cards with ethernet.

Do I need to issue user priviledges on the desktop for the shh client, or something like that?

I know this can be annoying, but I don't know a thing about the practical side of this all....:(

---

### Post by alamba on 2006-02-04
No user priviledges need to be mapped. openssh will allow you to pickup anything from your home directory.

A

---

