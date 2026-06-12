---
title: "What exactly does a server do?"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by Volume on 2009-12-14
Hello everyone.  I have been tinkering with my Ubuntu box for a while now, but I am at a loss as to how I can use Linux as a fileserver, and for backups and such.  I think part of my confusion is that there is so much information out there, I don't know where to start...

Can I start by asking what exactly a server does, and how it may go about doing it?  Also, where is good reading about how to setup a home server for storing my files (between Windows and Linux) and backing up?  What types of things can I do by setting up my linux box as a server to my other PCs?  What are the benefits?

I have 3 PCs, one with Ubuntu Linux (which I would like to be my "server") and 2 with Windows Vista x64.  

Thanks a million.

---

### Post by Iowan on 2009-12-14
[Here]("https://help.ubuntu.com/8.10/serverguide/C/index.html") is a server guide (for 8.10). It has some setup information, as well as a list of some things a server can do.

---

### Post by shairozan on 2009-12-14
Hey there, 

I figured I'd chime on what the server is and does. Whenever you perform a a function on your network and your computer has to ask another computer how to do it, or where to go, that is the primary function of the server. A server can have many functions, and here are some examples. 

[LIST=1]
[*]Mail Server - An email server is whatever you connect to when you startup outlook, or in most cases, you go to gmail or yahoo. The server does all of the work, but you just tell it where to send email and how. 
[*]File Server - A file server is practically a pack mule. It's sole purpose is to take files you provide it and keep it there. 
[*]DNS Server - The naming server basically takes [www.google.com](www.google.com) and translates that to an IP address that your router can do something with. Without this, you'd have to memorize the addresses for all of your favorite websites :-/
[*]DHCP Server - DHCP servers manage the IP Address space on your network so you don't have to worry about conflicts or manually assigning an address to every machine you have
[/LIST]

Any machine can do all of the above functions, but only after specific programs have been installed and configured. Server functions are basically just large programs. For file sharing, for example, a computer must run the samba application. For email, some will run postfix and some will run Zimbra, etc, etc. 

In regards to how to setup a file server, this document looks promising.

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

The biggest benefit to having any server is a central location to either (a) find files (b) control access or (c) control configurations. I will tell you that having a file server is a nice commodity, as once it's setup correctly you can access it from any machine on your network. It takes the question of "Where did I keep my files" out of the equation, especially if you are diligent about keeping important files there. 

Hopefully this answers some of your questions. Please let me know if you need anything else though!

---

### Post by Volume on 2009-12-14
Thank you for such quick responses, folks.  I had stumbled across the ubuntu server guide, which I am sure is an excellent and thorough guide, however it is too advanced for me at this point.

Right now I need something more along the lines of a description, and maybe some reading about what a server actually does (or how the software gets the hardware to interact with each other).  I think this would clear up a lot of my frustration.  I am not a noob to computers--but I have not ever set up or administrated a network.  I think that would be where I need help.

Any further suggestions?

Thanks again

---

### Post by bab1 on 2009-12-15
> **Volume said:**
> Hello everyone.  I have been tinkering with my Ubuntu box for a while now, but I am at a loss as to how I can use Linux as a fileserver, and for backups and such.  I think part of my confusion is that there is so much information out there, I don't know where to start...

Can I start by asking what exactly a server does, and how it may go about doing it?  
There are 2 definitions of what a *[S]erver* is.  The progammatic definition is: a service running in the background that responds to client requests for the specific service.  This would include DNS, DHCP, HTTP, Samba, LDAP, SSH, FTP, and many more.  These can all run on the same physical hardware (box) if you wish.

The second description is more pragmatic.  Any dedicated device for running of the above services is typically called a server.  Most OS distros (including MS Windows) optimize the kernel for the OS that is dedicated to server operation.  This does not mean that you can't run server services on a desktop, but you should consider which version of the OS you are using based upon what you intend to do with it.  

> 

Also, where is good reading about how to setup a home server for storing my files (between Windows and Linux) and backing up?  What types of things can I do by setting up my linux box as a server to my other PCs?  What are the benefits?

There is tons of reading material on the internet for the setup of servers (services) and for setting up Ubuntu Servers.> 

The main benefit is centralized management of services (all hosts use the same server services from one dedicated host).  In some cases you need the server (service) on each machine (e.g. SSH) for it to work.

> 
I have 3 PCs, one with Ubuntu Linux (which I would like to be my "server") and 2 with Windows Vista x64.

I would start with Samba for file sharing.  There are multiple ways to set Samba up, so you need to define for yourself how you wish to use it.

---

### Post by chaumurky on 2009-12-15
Looks like it takes two seperate people to kill a thread and scare off a noob...

:popcorn:

---

### Post by lisati on 2009-12-15
> **Volume said:**
> Can I start by asking what exactly a server does, and how it may go about doing it?  Also, where is good reading about how to setup a home server for storing my files (between Windows and Linux) and backing up?  What types of things can I do by setting up my linux box as a server to my other PCs?  What are the benefits?

OK to get back to your question before this discussion gets too horribly derailed by what appears to be a difference of opinion.

This is a quote from [http://en.wikipedia.org/wiki/Server_(computing](http://en.wikipedia.org/wiki/Server_(computing))

> In computing, a server is any combination of hardware or software designed to provide services to clients. When used alone, the term typically refers to a computer which may be running a server operating system, but is commonly used to refer to any software or dedicated hardware capable of providing services.


Edit: +1 to actions of staff member(s) who dealt with the difference of opinion that prompted this response.

---

### Post by revanb on 2009-12-15
Simple description of a server:

Firstly, a machine could be refered to as a server when its primary purpose is to run server software. But, any machine can run server software, a home pc too.

Basically, a server is a program which is running continually on a computer and listens on a port for request. When a request arrive the server responds and answers the request. For example, in easy terms, when you open a web page in a browser a request goes to the relevant web server and that server sends the web page to your computer.

Basically imagine your network as a postal service. When you want to send a message accross the network you need to put an address on the message and the person it must go to. This is where IP addresses and ports come in. An IP address is a set of 4 numbers seperated by dots. The numbers can range from 0-255 eg. 192.168.1.1 . On a network each computer needs an IP address so that it can be uniquely addressed. This is like a street address on a letter. 

But now on every computer there are many programs running. Each program needs to be individually addressable too. This is where ports come in. There are thousands of ports available on every computer and a port is basically a number. This like a persons name on a letter.

Web servers use port 80 by default.
FTP servers use port 21 by default.
SSH servers use port 22 by default.

So each of these services would be accessable on a computer by specifying its IP address and the port to use.

Try the following:
type [http://www.google.com:80/](http://www.google.com:80/) in a browser and it will work normally,
type [http://www.google.com:123/](http://www.google.com:123/) and it won't work.


By adding the  :80 or :123 we are specifying the port to use. For normal web server anything other that 80 will not work.

---

### Post by Volume on 2009-12-15
> **chaumurky said:**
> Looks like it takes two seperate people to kill a thread and scare off a noob...

:popcorn:

hahaha!  No, I'm not runoff!  I understand there are "differences of opinion", but even in my noobness that did not make any sense...

Thanks for all the input guys

---

### Post by Volume on 2009-12-15
Would anyone be able to suggest some books which may help with my endeavors?  I would prefer something not too detailed, so I don't get sidetracked, but with enough information that I can begin to grasp the concepts

Thank you

---

