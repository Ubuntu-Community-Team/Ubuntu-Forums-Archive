---
title: "Secure Shell Questions"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by lalanza on 2012-07-06
Hello, everyone. I've been dabbling around with SSH for a few days and I have a few questions for the gurus.

So far, I've been successful communicating between my local wireless network (2 laptops and iPhone), and have even been able to reach my laptop from outside of my network. I am using Ubuntu 11.10, OS X 10.5.8, and a jailbroken iPhone.

So, my questions are:

Is there a decent method of streaming audio/video as opposed to a secure copy and playing locally? *Can I use my iPhone to watch videos stored on upstairs laptop?*

How secure is this setup from an attacker? *I've set the config files to use a port other than 22 and disabled password prompts with generated keys to client/server.*

Is this the preferred method of setting up a proxy? *If I were using a computer at work-one with limited internet access- could I utilize this SSH setup to tunnel my traffic for unrestricted internet access?*

I appreciate any feedback

---

### Post by Kirk Schnable on 2012-07-11
> **lalanza said:**
> Is there a decent method of streaming audio/video as opposed to a secure copy and playing locally? *Can I use my iPhone to watch videos stored on upstairs laptop?*

I haven't found a good way to watch videos from an SSH server on an iPod\iPhone\iPad yet.  I've been sort of keeping an eye out for something like that too.  

On a Ubuntu client, you could mount your SSH server as an SSHFS and it would be like a local hard drive, you could watch all the videos easily.

> **lalanza said:**
> How secure is this setup from an attacker? *I've set the config files to use a port other than 22 and disabled password prompts with generated keys to client/server.*
Myself and a lot of people I know run vanilla SSH servers and they do just fine.  I certainly don't feel like my SSH server is a security hole.  

You may want to setup Fail2ban, to automatically ban IP addresses which fail login a few times.  That should keep brute force password attackers at bay.  
[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)


> **lalanza said:**
> Is this the preferred method of setting up a proxy? *If I were using a computer at work-one with limited internet access- could I utilize this SSH setup to tunnel my traffic for unrestricted internet access?*
I prefer to avoid using terminology like "preferred method", as everyone has their own preferences.

Personally, I have used SSH before to do something like what you're asking.  If your work client is a Ubuntu client, you can run this command to setup a SOCKS5 proxy:
```
ssh user@your.server.com -D 8080
```

You can now connect to 127.0.0.1:8080 as a SOCKS5 proxy, which is supported by numerous programs from FileZilla to Firefox.

All traffic through this SOCKS5 proxy will be tunneled through your SSH connection.

If you want to do this on Windows, I recommend PuTTY as the client.  The procedure to connect is similar: [http://martinjr.net/2010/06/29/quick-and-easy-socks5-ssh-tunnel-set-up-with-putty/](http://martinjr.net/2010/06/29/quick-and-easy-socks5-ssh-tunnel-set-up-with-putty/)



If you still have questions, don't hesitate to ask!

Kirk

---

