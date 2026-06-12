---
title: "Using gFTP to connect to SSH server"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by ZeldaFan on 2009-07-10
I need to access an SSH server for file transfer, so I installed gFTP. However, when I enter in the fields for the server name, user, and password, it says the protocol initialized, but it never actually connects. It's just perpetually "connecting"...how do I successfully connect?

---

### Post by jonobr on 2009-07-10
ftp and ssh are two different protocols,

you need to install an ftp server for ftp transfers.

If you have openssh installed though, you could use scp instead which is a lot more secure.

To copy files its easy to copy a file from your ssh server you would just to

scp myname@ipaddress:~/myfile .

or in english 
secure copy using username myname at machine ipaddress and copy from my home directory , a file named myfile and copy it to the current directory of the machine IM on(thats the . at the end)



To upload a file to your ssh server

its just 
scp myfile myname@ipaddress~/

---

### Post by ZeldaFan on 2009-07-10
As much as I can deal with the command line, I'd personally prefer a GUI interface for this b/c I'm not completely sure about the directory tree of the files I want to receive. They each contain an obscure string of letters and numbers that would be much easier to handle with a graphical interface.

---

### Post by jonobr on 2009-07-11
From a client using windows, you could use winscp it has a simple drag and drop interface

From an ubuntu machine, you could try something like secpanel,
same drag and drop although I have not used it myself.

OIn the commandline if you have complicated directories, you could user wildcrds

~/Desktop/my*/12*/43*/*.jpg

Or you could ssh to the server,

cd to the directory and then copy the path

or you could make symbolic links so you dont have to remmber path names

do on your home dire, you could have a symbolic link like 

~/targetdir

which is a sym link to

~/Desktop/file/here/in/this/subdirectory/I/want/to/copy

Lots of options, but again, if your guy inclined, the first is the best

Cheers

---

### Post by The Cog on 2009-07-11
I always prefer to do my first connect using ssh from the command line because it gives meaningful error messages if there's a problem. After that, I just use nautilus for sftp - type an address like this in the nautilus address bar:
**sftp://thecog@1.2.3.4/**
If you are using the same username both ends of the connection, you can omit the username like this:
**sftp://1.2.3.4/**

---

### Post by ZeldaFan on 2009-07-12
Secpanel seems pretty interesting, and I'll try it out as as soon as I can get to the server again.

---

### Post by ZeldaFan on 2009-08-12
I tried using both the command line and GUI (secpanel) and I just can't seem to connect. I'm not sure what I'm doing wrong...do I need to change the firewall settings?

---

### Post by jonobr on 2009-08-12
you should try posting the command your using.

I have never used secpanel.

Do you have openssh or similar installed to allow ssh/scp connections?

---

### Post by paulisdead on 2009-08-12
What exactly are you trying to do here?  Are you trying to get to your home box from work or elsewhere, or is this across the LAN?  If it's going out over the internet, is your router/cable/dsl modem configured to forward port 22 to the server?

GFTP fully supports SFTP, you just have to tell it to use port 22 (or whatever port you're running ssh on if you're using a non standard) and select SSH2 from the drop down menu.  SFTP is basically FTP over SSH, and is enabled by default in the SSH server, so you should be able to use it fine.

Filezilla is also another option, but I've had weird issues with it.

---

