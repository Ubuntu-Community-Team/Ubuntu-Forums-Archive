---
title: "Remote Sessions from Windows?"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by ocr14a on 2009-01-14
Hi. 
I have an Ubuntu server up and running, and I'd like to be able to connect to it remotely; kinda like I do with MS Remote Desktop to my Windows servers. 

I tried Xming (**[here's my thread about it]("http://ubuntuforums.org/showthread.php?t=1031716")**), but no luck there. 

Any chance there is a list of available methods here somewhere - with rankings, etc?

Thanks.
steven

---

### Post by ocr14a on 2009-01-15
Wow! 
Sometimes, in forums, I see bunches of replies right away, but now I haven't seen anything in either of my recent threads from the moment I started them.

Anyone?

---

### Post by blackened on 2009-01-15
> **ocr14a said:**
> Wow! 
Sometimes, in forums, I see bunches of replies right away, but now I haven't seen anything in either of my recent threads from the moment I started them.

Anyone?

Often it's just bad timing, other times it's just threads getting lost in the flood.

Do a forum search on putty and ssh. Should get you started.

---

### Post by stefangr1 on 2009-01-15
Xming is not a remote desktop client, but it is an X11 server that can be used to forward the graphics from a program that is running on a server to a client with xming.

You can use putty to login on your server when you have installed openssh-server. You can use vnc (install vnc4-server on the server, you can use a windows vnc client on the windows machine). Also, you have to forward the appropriate ports.

---

### Post by ocr14a on 2009-01-15
Thanks, guys. 
I have actually looked around and performed a number of searches, but I still haven't found quite what I'm looking for. 

I have used VNC for many years. So, I know what it is and how it works. 
It is not what I am looking for. 

I'm not sure if you've ever used Remote Desktop connections within the Windows world, but that's basically what I'm looking for in the Linux world. 

I don't just want a command line connection. 
I want to be able to log into my Linux server remotely, and have it be its own session (i.e. not just looking at or controlling another session which is already running on the server - though the ability to connect to an already running session would be nice too) and have exactly the same kind of GUI that I have when I log in locally. 

Does any such thing exist? 

Thanks again. 
steven

---

### Post by stefangr1 on 2009-01-15
Ehm... this would be vnc...

Have a look at this howto:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by ocr14a on 2009-01-16
> **stefangr1 said:**
> Ehm... this would be vnc...

Have a look at this howto:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

Aha. 
I see that VNC is much more useful outside of the Windows world (which is what I'm used to). 

Thanks. 

So, I see that the OP in that thread was last updated on Feb. 20 of 2006. Is it all still relevant, or should I look for a more recent thread somewhere? 

...or is there a 'document' on this?

steven

---

### Post by ocr14a on 2009-01-20
:bump:

---

### Post by tmetzcc325 on 2009-01-23
Even though the article is older, it is still a great way to set up VNC access.  And yes, VNC is much more robust on Linux hosts than Windows :)

---

### Post by Vesperatus on 2009-01-23
Have you tried the desktop sharing feature in Ubuntu ?
Following that, you should be able to achieve 2 things depending on what you pick under "Allow other users to view your desktop ). 

1- You will share the same desktop. 
2- You will start a separate session.

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")

---

### Post by cwmoser on 2009-01-23
I run Ubuntu at home and use Windows XP at work.  I found by far the best remote desktop package is NXServer.  Certainly you have to install the NXServer on the Ubuntu PC and NXClient on the Windows PC.  It is extremely fast -- much much faster than VNC.  Its secure as it uses SSH underpinings.

I remote into my home Ubuntu PC often to run QuickBooks, Open Office, Evolution, etc.

Personally, I don't think you will be pleased with the sluggishness of VNC.

So, I would recommend NXServer for GUI remote access.  You can also install putty on your Windows PC and get a remote command line console.  With the putty package are ftp and rcp commands to copy files off your home PC and onto your work PC.

Carl

---

### Post by Cosimix on 2009-01-23
[COLOR="Green"]**THIS IS A QUICK HOWTO FOR SSH X11 TUNNELLING**[/COLOR]

What I personally use and I love it because secure, is Cygwin X server for windows.

It is very easy to use and setup:

1. [http://cygwin.com/setup.exe](http://cygwin.com/setup.exe)

2. You don't need to install everything but only what you need (X server)

3. Enable X forwarding on your ssh server. Add this lines:
   
sudo nano /etc/ssh/sshd_config
   
 **  X11Forwarding yes**
   **Ciphers blowfish-cbc**     <<this is to set a fast cipher for encryption (facultative)***

4. Start the X server on windows

5. Enable X11 tunnelling in Putty, start an ssh connection username@ssh_server_ip and on the CLI to initiate the desktop session run the command:
**sudo /etc/init.d/gdm start**
***use this command to start the Desktop Manager, if it is not enabled at startup, check if it is already running: **ps aux | grep gdm**

**Note** there are many Desktop Managers for linux. GDM is Ubuntu's default. To save bandwidth I have installed [XFCE4]("http://www.xfce.org/projects/") as a quite lightweight one. 


***If you are not concerned about security (home private network), and want to use no encryption, you need to recompile OpenSSH with a '--with-none' option to allow for disabled crypto. The default builds use '--without-none' to force encryption. If you want to reduce overhead to a minimum, BLOWFISH is probably the way to go. I don't know to be honest how much overhead encryption causes. Nowadays PC should cope with it quite easily.

 [COLOR="Red"]SSH X11 TUNNELLING with _[XFCE4]("http://www.xfce.org/about/screenshots")_ BENCHMARK[/COLOR]

use **sudo iftop -i eth0** to monitor bandwidth consumption:

Results: When idle, bandwidth utilization is close to zero (peak 56-400kbps) and average is 5-6Mbps depending on the running applications

Have fun.

---

