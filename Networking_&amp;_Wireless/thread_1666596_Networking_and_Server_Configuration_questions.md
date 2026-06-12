---
title: "Networking and Server Configuration questions"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by computerguts on 2011-01-13
Hello, 
I have some networking and server configuration questions, any help would be greatly appreciated. I own a small business and recently I have been using the Opera web browser extension, "Opera Unite" as a web-server including media and other file types as well as a website. I have found that my business has grown out of the Opera Unite platform, and have some old computers lying around that would be perfect for running Linux,  most of them are old P4's. I need a way to turn one of these Linux computers into a web-server, to run a website and a file server, they need to be able to be accessed and edited from over the internet and not just one location. Also I need this computer to be able to connected my windows shares, or network drives as they are called in windows. Is there any program or combination of programs I can use to do this, and how would I configure them? 

Thanks

---

### Post by papibe on 2011-01-13
All of that can be accomplished by:

[LIST=1]
[*]Installing Ubuntu Server Edition.
[*]As a part of the installation process chose these packages:
[LIST=1]
[*]OpenSSH Server: to administrate your server remotely.
[*]Samba: to share files with windows clients
[*]LAMP: to use the machine as a web server (this one is several packages including apache, php and MySQL)
[/LIST]
[/LIST]

Here's more info: [FAQ about the Ubuntu Server Edition]("https://help.ubuntu.com/community/ServerFaq"), and [Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html").

Regards.

---

### Post by computerguts on 2011-01-14
Can you use Ubuntu Server Edition in a GUI and not only CLI? 
Im not very good with configuring networking with the command line interface. 

Thanks

---

### Post by papibe on 2011-01-14
Yes, you can either install a GUI, like gnome, on top of the server, or just install the desktop version of Ubuntu. All the programs I mentioned will also run on the desktop edition.

One important thing to consider: both the desktop and gnome on top of the server, need more resources. Usually that means more RAM and more HD space.

BTW, Have you thought in any software to develop your web site? If not, take a look at [Drupal]("http://drupal.org/"). Instead of "programming" you do more "configuring". Worth a look.

Regards.

---

### Post by drdos2006 on 2011-01-14
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by rbishop on 2011-01-14
I would also recommend using [http://www.webmin.com]("http://www.webmin.com/") .  It is a great piece of software that allows you to configure your server remotely from any web browser.

---

### Post by computerguts on 2011-01-14
Thanks for all the help, I will try each one out and let you guys know 

Thanks again

---

