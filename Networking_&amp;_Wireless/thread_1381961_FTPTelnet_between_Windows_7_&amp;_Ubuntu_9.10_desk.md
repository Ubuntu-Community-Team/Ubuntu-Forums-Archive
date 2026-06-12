---
title: "FTP/Telnet between Windows 7 &amp; Ubuntu 9.10 desktop"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by TorMike on 2010-01-15
Hi All,

I just installed Ubuntu 9.10 Desktop last night, successfully install apache2, MySQL 5.0 and PHP 5.0. great.

Now I need to communicate between by Windows 7 machine and my dual boot XP Pro/Ubuntu.  

I also have another computer loaded with Red Hat Linux with I successfully communicate using WinSCP and Telnet.  To complete the link between the Win 7 Machine and Red Hat all I did was add the Linux box to my HOSTS table (ie:  192.168.1.103  Mlinux).  Everything works fine.  I can copy files, test my websites FROM my Window 7 machine.

So I thought it would be the same with Ubuntu.  Nope!  The IP from my dual boot machine is 198.168.1.101 (confirmed using ifconfig) so I added it to my HOSTS table and I cannot connect vis WinSCP nor Telnet.

Should I have install Ubuntu server instead?  

Also kind of weird, I don't know the root password??? , but then again I don't remember being asked during installation for a 'root' password.

What's up with that.

All I want to do is test my website applications on a Linux box.

Mike in Toronto

---

### Post by Grenage on 2010-01-15
Make sure you have SSH installed:

```
sudo apt-get install ssh
```

> Also kind of weird, I don't know the root password??? , but then again I don't remember being asked during installation for a 'root' password.

What's up with that.

Ubuntu doesn't use a root account logon, it's done via sudo.  I'd tell you how to set a password, but I'd be breaking forum rules (it's generally safer for new users).  If you really need it, google and you'll get an easy answer.

I personally ssh with my user account and then use sudo.

---

### Post by Belizeian on 2010-01-15
As a rule FTP and telnet are bad.  Clear text user/password with them like he said use SSH for terminal and winscp for ftp like file manangement.  Disableing ftp and telnet are like the first thing I do when I admin a box.

---

### Post by TorMike on 2010-01-15
Install SSH and it works like a charm.

My WinSCP and Telnet sessions are working.  I'm not a network guy, as you can tell, I just develop code for website and I really needed to get my test site up and working.

I'm used Red Hat Linux but got tired of paying for Unix and hear about Ubuntu from a friend.  Amazing so far.

As for the root password.  I'm a control freak and thought I needed it to set up MySQL until I realized that might not be necessary.  Haven't tried it yet but I'm going to have to modify my php / apache2 config files to set the environment I used to working under.  If I don't need root access then nothing to worry about.  HOWEVER, what if I need to modify my HOSTS files???

Thanks for all the help.  I better get busy.

---

### Post by Grenage on 2010-01-15
If you need to edit an Ubuntu host file, you can do so using *sudo* - both in command prompt or gui:

```
sudo vim /etc/hosts
```

or

```
gksu gedit /etc/hosts
```

> hear about Ubuntu from a friend. Amazing so far.

While I don't think Ubuntu is the magical sword of Linux, the community support is imho unmatched.  Welcome!

---

### Post by TorMike on 2010-01-15
As an absolute newbie to Ubuntu and I have run into my first problem.

Is sudo a magic command?

I was trying to find the httpd.conf and php.ini files to modify for my environment and I think I found them, well php.ini at etc/php5/apache2/php.ini but the file under /etc/apache2/httpd.ini is emtpy, yet [http://localhost](http://localhost) resolves to /var/www.

So I thought I'd just create a directory under [www..]("http://www.."). permission denied! Of course since I'm not root so I can't create a directory and then change the permission to user Mike, that's me.  So short of 'creating' a root password, what's the solution, the magic sudo command?

These is what I really hate about 'third party' installs, where are my config files.

Tried unix find . -name httpd.conf and find . -name php.ini to locate the files but they don't seem to be the files I need.

Hate to complain but it should not be so hard to set up a simple environment.  Apache2/PHP/MySQL are really easy to use if you configure them correctly.

Maybe it time to move this thread to another forum?

---

### Post by Grenage on 2010-01-15
It is a magical command of sorts, it means **su**peruser **do**.  Basically whatever follows it gets run with root permissions.  For example:

In a terminal:

```
sudo mkdir /var/www/newfolder
sudo mv /var/www/newfolder /var/www/files
sudo chmod xxx etc
```

In the GUI:

```
gksu nautilus
```

This opens the nautilus file manager with root rights, so be careful!  gksu is basically the sudo for gui tools.  Although sudo will work, gksu is safer.

Unfortunately my experience with Apache is limited, so I cannot help there.  I believe there is an Apache or LAMP forum around here though.

---

