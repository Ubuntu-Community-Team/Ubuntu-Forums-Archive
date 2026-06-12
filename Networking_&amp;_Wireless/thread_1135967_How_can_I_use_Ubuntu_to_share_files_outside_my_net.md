---
title: "How can I use Ubuntu to share files outside my network?"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by suprecook on 2009-04-24
Hello my name is Danny Alaiev, and I have been using Ubuntu for a couple of months. I think it's great. I have been needing to share files with computers on OTHER networks for a few reasons and I looked all over the web and I didn't find anything. What I'm trying to do is use my Ubuntu machine like a server so share files with computers on OTHER NETWROKS. Something like: I type in a URL on another computer and It acesses my harddrive so the computer I'm on can download stuff off of it. Just to clarify [COLOR=Red]I DONT WANT TO SHARE FILES OVER A NETWORK, I WANT TO SHARE FILES OVER THE WEB FROM COMPUTERS ON TWO DIFFERENT NETWORKS WITHOUGHT USING A[/COLOR][COLOR=Red] STORAGE SITE!!![/COLOR]

---

### Post by doas777 on 2009-04-24
well, that is not a simple question, and depends on the hardware you have available.

first off, do you have a router, and/or multiple PCs at each site?
if so, does it have NAT or DMZ features?

do your internet connections at each site have static IP addresses?
if not, look into [http://www.dyndns.com/](http://www.dyndns.com/)

how would you estimate your comfort and understanding with network technologies, and ubuntu?

---

### Post by doas777 on 2009-04-24
my recommendation is to use ssh for connecting across the Internet.
its about as safe as remote access daemons get.

once set up, a user could connect with nautilus(gui) or ssh (commandline) in ubuntu, or with winscp (gui file manager) or putty (command line terminal).

the basic algorithm, is:
1) install opensshserver on the server ([https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto))
2) edit the router configuration to forward the ssh port ([http://portforward.com/](http://portforward.com/))
3) test connecting from a client

hows that sound?

---

### Post by suprecook on 2009-04-24
The computers I am going to be accessing ubuntu from run windows will ssh work with that?

---

### Post by doas777 on 2009-04-24
> **suprecook said:**
> The computers I am going to be accessing ubuntu from run windows will ssh work with that?

yep. you'll want to use winscp to connect. 

[http://en.wikipedia.org/wiki/WinSCP](http://en.wikipedia.org/wiki/WinSCP)
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

theres no really reliable way to run samba (windows file sharing) over the internet without things like VPNs and whatnot, so ssh is the best bet.

ftp would also work, but ftp is pretty rare anymore (for good reason) and is a somewhat more complex setup server side.

what do you think?
I will be offline for a few hours, but ill check back later tonight. I;m a nightowl on the weekends...

---

### Post by suprecook on 2009-04-24
Thanks alot, I have one last question, what are other ways of sharing files?

---

### Post by bladeswords on 2009-04-24
You could use things like FTP server, or even a web server would work fine.  But I wouldn't recommend sharing your whole system like that...

---

### Post by doas777 on 2009-04-24
there are many many ways to do it, but when it comes to internetwork transfer you are pretty much stuck with either web protocols (http, ftp, irc, emule, bittorrent, etc) or tunneling protocols (ssh, vpn, etc) that allow you to connect like you are part of the remote network. 

there are many more. the reason I suggest ssh, is because it requires only minimal configuration, and is as safe as possible. VPN requires heavy network configuration, and web protocols require advanced server configurations (and will not give you access to your whole hard disk anyway). installing and configing ssh takes mabey 5 minutes. apache is not so easy.

---

### Post by suprecook on 2009-04-24
Thanks alot but ssh looks complicated can you point me towards an easier guide?

---

### Post by doas777 on 2009-04-24
you're right, that guide is far more complex than i had recalled.

basically all you need to do at a minimum is open a terminal and enter:
```
sudo apt-get install openssh-server
```

when that is complete, we need to check a setting in your ssh configuration file. open it with:
```
gksu gedit /etc/ssh/sshd_config
```

look for the line that says:```
PermitRootLogin yes
```
and change 'yes' to 'no', save and close. 

now we need to reload ssh with:
```
sudo /etc/init.d/ssh restart
```

now try to login to it to test with:
```
ssh 127.0.0.1
```
and give your password when asked. if it connects than it's up and running. you should also be able to connect with a gui, by opening a nautilus and putting in the address bar:
```
ssh://127.0.0.1
```

ok, a quick disclaimer. this is a pretty default ssh configuration. I have to recommend you look into security options for ssh to find the right security balance for your needs. I never expose ssh to the Internet, so i don't worry so much about locking it down. i just block port 22 on my router to keep people out. 

that is all that is really needed to get ssh working. if it were me, I wouldn't give anyone else a username/password for an account with administrative (sudo) capability.  

so that is step one. once your there, or if you have trouble post back, and we'll move on to the router. 

have fun,
franklin

---

### Post by suprecook on 2009-04-26
Everything Worked and there is an icon on my desktop. Took me a while but it was worth it. I think I'm ready for the next step. 

BTW I'm sorry it took me a whole day, I had a surgery done.

---

### Post by suprecook on 2009-04-26
Please reply as son as possible

---

### Post by albinootje on 2009-04-26
> **suprecook said:**
> I DONT WANT TO SHARE FILES OVER A NETWORK, I WANT TO SHARE FILES OVER THE WEB FROM COMPUTERS ON TWO DIFFERENT NETWORKS WITHOUGHT USING A STORAGE SITE!!!

Sounds like you want to run VPN software on both firewalls on the two different websites.

I've done this a few years ago with M0n0wall on two different firewalls. 
It is required that both networks use a different network range.

This could be useful to read : [http://en.wikipedia.org/wiki/OpenVPN](http://en.wikipedia.org/wiki/OpenVPN)

---

### Post by suprecook on 2009-04-26
I think I'm gonna stick with ssh

---

### Post by doas777 on 2009-04-26
sorry about the delay, and I hope your procedure went well.

ok, the next step is to configure your router to accept incoming connections to ssh, and to pass them on to your PC.

what kind of router do you have?
this site, has port forwarding instructions for most routers out there.
[http://portforward.com/](http://portforward.com/)

first we want to pick an arbritrary tcp port above 1024 but below 49000 (or so, i forget the exact number). I suggest 7630 because it is not reserved according to iana. 
This port number will be your outside port for accessing ssh. clients would connect to it.

next your router will forward the request to your host, at tcp port 22, and connect to ssh.

look up your router at the link above, and follow the instructions to map tcp/7630 outsite to the ssh hosts tcp/22. 

once this is done, or if you do not have a router, simply go to: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)
and put in 7630 if you have a router and  22 if not. 
now try to connect to the port as you did before, but use the IP address you see on canyouseeme instead of 127.0.0.1.

if you can see the port, then this step is complete, and it;s time to move onto clients.

have fun, and post back if you have any trouble, or are ready to move on.

---

### Post by doas777 on 2009-04-26
ok, on to clients. 
For windows, the two most common utilities for connecting to ssh are  [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") and [WinSCP]("http://winscp.net/eng/download.php")

PuTTY will give you a command line interface, suitable for any cli task that the user is allowed to commit. sudo capable accounts will be able to administer the system, so be cautsious about the accounts you give to others.

WinSCP, allows you to browse the filesystem, download, and upload files, and edit text files with a built in editor (this last one made my life much easier in college when I was less confortable with the command line).

with either program you want to connect to port open on the outside of the router, as we discussed in the last step. 
ex:
```
<serverIP>:7630
```


for ubuntu clients, just use ssh at the command line, or type the ssh address into the address bar of a nautilus window, in the form of;
```

ssh://<servername/ip>:7630/home/<username>

``` 
to connect and start at your home directory.

with luck, that should do it. post back if you have any problems, and to let us know how it works out for ya,

have fun,
franklin

---

### Post by rgl2020 on 2009-04-26
I agree ssh is probably the best and easiest way to go for you.  You might want to tighten up your security with denyhosts after you finish setting it up

[http://ubuntuforums.org/showthread.php?t=450853&highlight=denyhost](http://ubuntuforums.org/showthread.php?t=450853&highlight=denyhost)

---

