---
title: "Looking for an FTP serve solution similar to Filezilla Server"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by iconoclast hero on 2011-04-05
I would like to know if there is an FTP installation similar to the way filezilla works where there is a standalone server interface that can work across platforms.  E.g. I would like to be able to have a server interface that was able to access the FTP server from windows and ubuntu.  I found a few links but my understanding is that there is not a linux version of filezilla and there is just so much information that is out of date.

Thanks

---

### Post by 1clue on 2011-04-05
I'm not familiar with filezilla, but there are lots of FTP clients and servers for Linux, and FTP is an open standard so they all work with one another.

---

### Post by iconoclast hero on 2011-04-05
I have looked at PureFTP and ProFTPd but I was hoping someone could point me toward one that has a cross-platform interface.

---

### Post by Joe of loath on 2011-04-05
Ummm

FTP IS a cross platform interface. Or rather, is a cross platform protocol.

---

### Post by iconoclast hero on 2011-04-05
> **Joe of loath said:**
> Ummm

FTP IS a cross platform interface. Or rather, is a cross platform protocol.

Yes, I know; I've been using it for decades.  I used to use Bullet Proof FTP server in Windows (BPFTP) but switched to FileZilla server.  As for clients, I've used CLI, FlashFXP, FireFTP plugin, and FileZilla.  

What I am looking for is a cross-platform interface for an FTP server.  With FileZilla, the server and the server interface are separate programs.  You can simply point to the server at startup with the correct password and it is the same interface every time.  It is also a GUI menu-driven interface.  I was simply hoping that something like that would allow me to interface with an FTP server from both linux and windows.

---

### Post by Joe of loath on 2011-04-05
Oh, so you're looking for a cross platform FTP client?

---

### Post by 1clue on 2011-04-05
You need a cross-platform GUI ftp client then.

Does it need to be full featured?  Firefox is a cross platform FTP client with a consistent interface on all platforms, but it's a PITA if you need to upload or delete.

I don't mean to be rude here, but it seems to me that if you want something just like Windows then you should be using Windows.  I'm not telling you to buzz off, I'm just saying that Linux is different because it's designed around a different philosophy, and so the software is all different.

I guess I'm in the dark ages here, because for me the command line client is most convenient, in which case it's very close to the same exact thing on any platform.  Well, and besides not using Windows for anything.

There are lots of GUI clients with convenient interfaces, even allowing server-to-server transfers by dragging from one place to the other.  I have no idea what's current, and can't remember the favorite I had back then I was using that sort of thing.

---

### Post by iconoclast hero on 2011-04-05
> **Joe of loath said:**
> Oh, so you're looking for a cross platform FTP client?

Nope.  (FireFTP would probably be my choice for a cross-platform FTP client if already using FireFox.)  What I want is a server administration front end/interface that can be used in both windows and linux.  

See [http://www.howtoforge.com/proftpd_web_interface_gui_tools](http://www.howtoforge.com/proftpd_web_interface_gui_tools).  You see how there are multiple front-end/administration programs that work with ProFTPd?  I am looking for a solution like that that also has an interface for administering the server in Windows.  

From the FileZilla Server FAQ:

> **  FileZilla Server FAQ **

 
[LIST=1]
[*]**I've just installed the server and after starting the interface, it asks for a server address.**
Despite administrating the server on the local machine, the interface  can also be used to administrate remote servers. But you will most  likely want to administrate your local server. In this case enter  127.0.0.1 as server address. For the server port, you have to enter the  same port number you did specify during installation for the admin port.  (default: 14147)
[/LIST]


I know that I could SSH into the server and adjust the FTP settings via the CLI but I was hoping I didn't have to do that.  I guess that is not going to be an option.

---

### Post by iconoclast hero on 2011-04-05
> **1clue said:**
> You need a cross-platform GUI ftp client then.

Does it need to be full featured?  Firefox is a cross platform FTP client with a consistent interface on all platforms, but it's a PITA if you need to upload or delete.

I don't mean to be rude here, but it seems to me that if you want something just like Windows then you should be using Windows.  I'm not telling you to buzz off, I'm just saying that Linux is different because it's designed around a different philosophy, and so the software is all different.

I guess I'm in the dark ages here, because for me the command line client is most convenient, in which case it's very close to the same exact thing on any platform.  Well, and besides not using Windows for anything.

There are lots of GUI clients with convenient interfaces, even allowing server-to-server transfers by dragging from one place to the other.  I have no idea what's current, and can't remember the favorite I had back then I was using that sort of thing.

No, again, I'm looking to be able to administer the server from another computer running windows.  I do find CLI to be easier in some instances but a GUI/menu-driven system for something I need to tinker with once or twice a year is going to be significantly easier for me to remember what to do.  

To put it another way:  I don't need info on an FTP client, I'm good on that.  I presently have 2 windows and 2 ubuntu machines.  One of the windows machines was my FTP server.  I have migrated all of the files that were hosted by the windows FTP server to my ubuntu 10.10 server box.  I would now like to make that my FTP server so they don't both have to run.  I would like to be able to interface (administrate, front-end) with the ubuntu FTP server to control user access, shared directories, etc., from my ubuntu desktop laptop and the windows computers.  Yes, I know that I can SSH and modify the config files, but I wanted to know if anything existed that would GUI front-end the server on both ubuntu and windows (not something to use to transfer files).

---

### Post by 1clue on 2011-04-05
Oh, for some reason I missed the "administer" part.

Try Webmin.

For some obscure reason Ubuntu doesn't have it in their repository, but it's a web-based front end for server administration.  Kicks the proverbial donkey.

*Edit:*
Excuse me, it kicks the proverbial donkey's *posterior.*

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by iconoclast hero on 2011-04-05
> **1clue said:**
> Oh, for some reason I missed the "administer" part.

Try Webmin.

For some obscure reason Ubuntu doesn't have it in their repository, but it's a web-based front end for server administration.  Kicks the proverbial donkey.

*Edit:*
Excuse me, it kicks the proverbial donkey's *posterior.*

[http://www.webmin.com/](http://www.webmin.com/)

Ok.  I took a quick look at webmin and if I understand properly the solution would be to front-end to webmin and the backend FTP would be ProFTPD?

---

### Post by 1clue on 2011-04-05
You can install whatever FTP server seems most appropriate, get the webmin module for that, and then there is a GUI configuration panel that you hit with a web browser.

This is GPL software, there is some FUD out there claiming that it's got a non-open license.  Not true.  I have no idea why Ubuntu doesn't have it in their package manager.

Last time I used it, it was really easy to set up and administer.  You can add visual themes to find the look you like, and I personally think most web-based routers and file servers use webmin to configure their stuff.

There are some software packages which don't have a webmin module, so look before you install.

---

### Post by iconoclast hero on 2011-04-05
> **1clue said:**
> You can install whatever FTP server seems most appropriate, get the webmin module for that, and then there is a GUI configuration panel that you hit with a web browser.

This is GPL software, there is some FUD out there claiming that it's got a non-open license.  Not true.  I have no idea why Ubuntu doesn't have it in their package manager.

Last time I used it, it was really easy to set up and administer.  You can add visual themes to find the look you like, and I personally think most web-based routers and file servers use webmin to configure their stuff.

There are some software packages which don't have a webmin module, so look before you install.

Ok, I kicked the tires a bit on their demo website and it looks like regardless of what I want to configure it would be a great front end for a lot of things.  I only said ProFTPD because that was what they have set up at the demo site.  I was going back and forth between ProFTPd and PureFTPd.  I liked what I saw at PureFTP but when I saw this, [https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP) I said, there has got to be an easier way for me to do this.  I just don't get my hands dirty with the FTP server often enough to learn the commands.  Basically I have it open so I can grab stuff remotely.  It also seems faster sometimes to move things that way inside my network.

Thank you, sorry I wasn't being clear enough initially about what I needed.

---

### Post by iconoclast hero on 2011-04-06
Thanks, I got ProFTPd running with Webmin running the front end.  I have not tested it on windows but I think this is a solution to my problem.  I wasn't looking for a web-based solution, but it works just fine.

---

