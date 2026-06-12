---
title: "Can't SSH to Xubuntu from Macintosh...?"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by muzungu on 2006-06-22
I've got an Xubuntu install on my Apple Airport wireless home network, along with three other Macs. After reading through this helpful guide:

[http://software.newsforge.com/article.pl?sid=06/05/31/1416242](http://software.newsforge.com/article.pl?sid=06/05/31/1416242)

I'm able to connect to each of my Macs via gFTP and the standard SSH client package. I had thought that by installing the open SSH server package I would also be able to connect to my Xubuntu machine from any of the Macs, but for some unknown reason I can't!

The error I get (using either the Mac OS terminal or an FTP app) is simply "connection refused". I installed Firestarter on my Xubuntu machine and when I saw the incoming connection attempts I authorized the source, but still no luck in connecting.

The other weird thing is that in the 'Shared Folders' system setting I can only set up my home folder as an NFS or SMB share... Shouldn't SSH be an option there as well? All I really want to do is be able to transfer the odd file back and forth. And setting up NFS or SMB on my Macs seems like overkill from what I've read...

Thanks in advance for any and all suggestions with this!

:confused:

---

### Post by gunderwood on 2006-06-22
I think your problem is that you're trying to connect to a SSH server with a FTP client. They are different protocols thus requiring different clients. Of course I'm not very familiar with Mac's so I'm assuming that when you speak of a command line OS X client you mean an FTP client. Because I am not familiar with macs I can't really help you on the client side other than telling you to try putty or some sort of SSH client to connect. Or when connecting with gFTP to specify the sftp:// protocol (Secure File Transfer Protocol). I can't remember if gFTP supports the protocol you'll have to check thaqt yourself, it's been a while since I used it.

I can although help you ensure that your SSH server is operating and accesible. 

First off we should ensure that the client is running on the Xubuntu box. To do this go to a terminal and type

```
ssh localhost
```

This should give you a login prompt to your machine. You should be able to login to your machine with your normal credentials. If you can do this this will confirm that the SSH server is running and that you can login. 

Next you need to find out if the firewall or some other networking factor may not allow a to the xubuntu host form your other hosts. The best way to do this is with a port scanner, try nmap, it's free and a great tool. [http://www.insecure.org/nmap/download.html](http://www.insecure.org/nmap/download.html)

N map will allow you to see what services are available on your hosts. So you're gonna want to scan your xubuntu host from one of your Mac hosts with a command something like this:

```
nmap 192.168.100.10
```

but substitute the xubuntus hosts ip for the one in the above argument.
You should get an output something like this:

```

Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2006-06-22 19:31 PDT
Interesting ports on celestine (192.168.100.10):
(The 1667 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
143/tcp  open  imap
445/tcp  open  microsoft-ds
5432/tcp open  postgres

```
 
If you get the listing for the SSH port then you know that you can reach the server from your host, therefore your problem is with the client and you need to find a SSH/SFTP client. If any of the troubleshoting steps don't work out like I described then your problem is some sort of configuration, networking, routing type stuff. If so post your results and we'll go from there.

Greg

---

### Post by muzungu on 2006-06-23
> **gunderwood]I think your problem is that you're trying to connect to a SSH server with a FTP client. They are different protocols thus requiring different clients. Of course I'm not very familiar with Mac's so I'm assuming that when you speak of a command line OS X client you mean an FTP client.[/QUOTE]

Hi Greg,

Sorry if I wasn't clear said:**
> ```
ssh localhost
```

If you can do this this will confirm that the SSH server is running and that you can login.

Yup, that worked -- though I did get the message "authenticity of host '127.0.0.1' couldn't be established - do you wish to continue?"... That's pretty standard, I guess? Seems a bit odd that Linux isn't self-aware. ;)
 
> Next you need to find out if the firewall or some other networking factor may not allow a to the xubuntu host form your other hosts. The best way to do this is with a port scanner, try nmap, it's free and a great tool. [http://www.insecure.org/nmap/download.html](http://www.insecure.org/nmap/download.html)

Yikes... I've been using Macs for more than a decade, but compiling a UNIX app in OS X with an Apple Developer key and/or FINK is a little too daunting, even for me! :shock: 

Now I *did* quite easily manage to install nmap on my Xubuntu machine, and run the scan on one of my Mac hosts -- that connection was categorically blocked, making me wonder if there's something in my Airport base station (i.e. wireless router) settings which is mucking things up. There is a firewall there, but I've allowed connections through SSH/Port 22. Strange...

Part of the problem is that Mac OS X dumbs a lot of this stuff down, so that I feel *extra* stupid when trying to get the same things working in Linux.

Thanks for your help, anyway. At least I can drop files to any of my Macs from this Xubuntu machine if not the other way 'round...

---

### Post by alxwind on 2007-02-04
The problem is that all ubuntu versions don't have openssh server installed by default. weird i know.
```
sudo apt-get install openssh-server
```
[IMG]http://img253.imageshack.us/img253/6973/picture1ae0.png[/IMG]

---

