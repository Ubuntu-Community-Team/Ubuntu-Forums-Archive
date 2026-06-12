---
title: "Access Ubuntu Desktop Remotely"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by finsyourfriend on 2010-02-16
Greetings all.

   I currently have a home network set-up with a Dell Poweredge 750 Server ( Intel Celeron, 1 GB RAM, 250GB SATA HDD, 32-bit OS) running Ubuntu-Linux Hardy Heron 8.04, a generic clone-case my father built for me (AMD Athlon 64, 2GB RAM, 160GB IDE HDD, 32-bit OS) running Windows XP Professional, and a Compaq Presario C700 laptop (Intel Pentium Dual Core, 1 GB RAM, 120GB HDD, 32-bit OS) running Windows Vista Home Premium. I want to be able to access my Linux desktop remotely, as in over the internet - from my laptop. :D 

   I have successfully accessed my Ubuntu desktop from my Vista laptop by installing and configuring TightVNC and Putty, but only at the local level. ;) 

   I have an AT&T 2Wire Gateway that has an internal built-in firewall, but I'm not sure how to correctly configure the firewall to forward Port 5900 to the Ubuntu Desktop, as from what I've read, this needs to be done. :confused:

Any ideas or more information needed, let me know. ;)

---

### Post by finsyourfriend on 2010-02-16
More info: All of these machines are networked on the same workgroup, can talk to reach other, and are configured for file sharing as well as sharing an HP printer attached to the Linux server via USB. :D

---

### Post by kouter on 2010-02-16
You've really done all the hardwork, lol.

Get on google or AT&T's website and search for the model of your gateway, looking of course for the manual.

That should give you the info you need to set up port 5900 to be forwarded.

You can also try for just a generic howto port forward guide on google, too. I got a few related hits for both, just don't know what model gateway you have.

---

### Post by prshah on 2010-02-17
> **finsyourfriend said:**
> 
   I have an AT&T 2Wire Gateway that has an internal built-in firewall, but I'm not sure how to correctly configure the firewall to forward Port 5900 to the Ubuntu Desktop, as from what I've read, this needs to be done.

There are a number of 2wire models, please see [www.portforward.com](www.portforward.com) for instructions specific to your model number.

After port forwarding (yes, you are right, it needs to be done), you should also setup a dynamic dns client (or check if the modem supports dynamic dns reporting). Post back if you need more information about this.

---

### Post by finsyourfriend on 2010-02-17
OK. I used the tutorial to set up the port to be forwarded, now the only thing that remains is to test whether it works or not. Do they make a Linux version of PFPort Checker? Aside from that, should I just jet down to the local coffee shop and see if I can access the server?

---

### Post by finsyourfriend on 2010-02-17
One more thing: the port shown in the firewall has the private IP address of my router listed. There wasn't an option to change the IP address to it's public one in the tutorial on PortForward.com This has me concerned the more I think about it...:frown:

---

### Post by adam814 on 2010-02-17
Forwarding port 5900 is NOT a secure way of accessing your desktop remotely.  VNC sends everything (including passwords) in the clear (no encryption at all).  I wouldn't want my password going across the wire like that as plain text.

Better yet tunnel it using SSH, which will encrypt everything for you.  It's a little tricky the first time, but it's easier than reinstalling because the script kiddie across the street was able to sniff your password and locks you out of your system.

This page should at least point you in the right direction:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by finsyourfriend on 2010-02-18
Adam814: Please re-read the first post in my thread: I already have the openssh-server package installed and the Remote Shell Server (SSH) Service running in Ubuntu and I'm using PuTTY in Windows for a secure connection  so back to my question:

How can I access the machine using the current set-up I have; meaning Remotely? I can already access the machine inside my local network using PuTTY and Remote Desktop in Ubuntu; I just want to do the same thing remotely. Anyone out there with experience with these programs please let me know...

---

### Post by prshah on 2010-02-18
> **finsyourfriend said:**
> already have the openssh-server package installed and the Remote Shell Server (SSH) Service running in Ubuntu 

How can I access the machine using the current set-up I have; meaning Remotely? I can already access the machine inside my local network using PuTTY and Remote Desktop in Ubuntu; I just want to do the same thing remotely. Anyone out there with experience with these programs please let me know...

There are a few misconceptions in your setup.

Putty allows you ssh access to your machine; it is a command line access only. It has nothing to do with GUI.

SSH is a secure transfer protocol that has nothing to do with VNC (or Port 5900 access). Just by installing an ssh server and connecting to it with putty does not automatically secure your VNC (remote desktop) connections. Adam is correct in that you should not port-forward 5900. You should port forward only your SSH port.

As a next step, you should get your "public" (ie, WAN) IP address. Then, use a different Internet connection (different from the one your ssh server is on) to check if you are able to successfully putty/ssh to your computer. You can consider using a dynamic dns client. Post back if you want more details on this.

If you are able to ssh to your server, you need to enable the use of tunneling. You can then forward local ports on the system you are sitting on to use remote ports on your computer via ssh, and THEN use tightvnc/vnc compatiable viewers with the local port to get encrypted remote control sessions.

For more details, including example screens and settings, please see example #3 in [http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html) . Please post back here if you run into problems.

---

### Post by finsyourfriend on 2010-02-18
OK; I followed the instructions to a "T" here: ](*,)

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

That being said, Prshah and Adam, can you post detailed instructions on how you remotely access your desktop?? :-k

---

### Post by finsyourfriend on 2010-02-18
PRShah,

Thank you for that link to VNC over SSH2. I'll be looking into that information after I get off of work, but it looks like I'll be able to access my machine remotely AND securely with these instructions. Thanks again.

Jon

---

### Post by finsyourfriend on 2010-02-18
PRShah,

After looking through your link, I may have spoke too soon. Comparing those instructions to the ones on Techotopia, they seem extremely confusing and code-driven. Simply put, all I want to do is access my desktop remotely. I know a lot of advice has been given on that, but skim through the Techotopia article and see if that isn't correct. I liked it up until this point and it talks about using a secure connection with Windows and Ubuntu. If that can work, that's fine. Please advise.

Thanks.

---

### Post by adam814 on 2010-02-18
The part of the TechTopia article for secure access from Windows using PuTTY is decent at least.  I haven't really read the other ones.

No one's saying you can't activate the remote desktop from Ubuntu like in that article (although with that you have to be logged in locally for it to work) or PuTTY to connect from a Windows machine.  It's just a REALLY bad idea to share it by forwarding your port 5900 in your router, instead use the SSH tunnels like in the article you mention.

P.S. I would also check the box for "only accept local connections" in the Remote Desktop wizard.

---

### Post by finsyourfriend on 2010-02-18
Adam,

Being logged in locally is not a problem since I leave the server on 24/7. ;) 

That being said, with the other research I have done here, a lot of people are asking for a equivalent to logmein for Ubuntu, which is exactly what I want to do - however, I know LogMeIn doesn't support Linux.  :frown:

What do you think of NTRConnect for Linux? - seems like you don't have to do any port mapping or firewall altering with it.

---

### Post by finsyourfriend on 2010-02-18
Found a work-around: Install LogMeIn on the Windows XP tower and Vista laptop, access the Windows XP tower from the Vista laptop via LogMeIn, and then access the Ubuntu server via VNC from the XP tower within the LAN - no port forwardig needed. :D

---

### Post by finsyourfriend on 2010-02-19
FYI Guys: After installing LogMein on each Windows machine and logging over the Internet to access the XP PC and VNC to the Ubuntu server, LogMeIn would crash the Vista laptop and, after shutting down the XP machine and rebooting, I found myself with a black screen after the Windows XP Splash screen on my tower. :-x 

So, to fix: I wentinto Safe Mode, looked under Display adapters and deleted LogMeIn mirror driver. Rebooted, and all was well for XP. ;) 

So, to close this thread: I was able to remotely access my Ubuntu server VNC from my XP desktop through a remote desktop connection from my Vista laptop by downloading and installing TeamViewer ([www.teamviewer.com](www.teamviewer.com)) on both Windows machines - works prefectly. \\:D/ 

I know people have high reviews of the software and it's used in commercial applications, but my first impression of using LogMeIn to VNC to Ubuntu: absolutely sucks. :-&

---

