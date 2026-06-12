---
title: "Need help with remote access."
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by Duckking man on 2013-06-18
So I have a text-file I need to get from a computer running WattOS.  Can someone tell me how I can get this file?  I know how to obtain my wireless router's IP address and I can get someone at the physical computer to turn it on.  I only need CLI access to do this.  I cannot recall what software is still on this machine.  Is there any basic utility that would let me log into my account on this machine as if I were there?  The computer I am using to do this is running ubuntu 12.04.

---

### Post by TheFu on 2013-06-18
> **Duckking man said:**
> So I have a text-file I need to get from a computer running WattOS.  Can someone tell me how I can get this file?  I know how to obtain my wireless router's IP address and I can get someone at the physical computer to turn it on.  I only need CLI access to do this.  I cannot recall what software is still on this machine.  Is there any basic utility that would let me log into my account on this machine as if I were there?  The computer I am using to do this is running ubuntu 12.04.

Never heard of WattOS before, but google says it is a lite-Ubuntu distro.  That means you have all sorts of remote access methods available, provided you can get the software and service enabled on the remote machine and get the firewall rules between your machine and the other one opened enough to support the remote access method that you choose.

The best remote access for **any** UNIX/Linux system is ssh. It is secure and very capable. There are file transfer methods built-into ssh - scp and sftp.  This link should help with getting the software installed that you need on the remote machine.
[https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)

You will probably want to secure the ssh connection - there are many techniques for that - I use seven. [http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) explains.  If all you do is install and configure **fail2ban** on the machine running the sshd server, then you'll handle 99.9999% of the security issues.

There are hundreds of scp/sftp/ssh how-to articles on the internet, so i won't bore you with that.

Good luck!

---

### Post by Duckking man on 2013-06-18
Thanks, I am reading the links you gave me.  There is one thing I realized I forgot to put in the original question.  I don't want anyone to actually log into the machine except for me as I have no other accounts set up.  Your answer won't require somebody else logging into the machine I need to get the file from will it?

---

### Post by Lars Noodén on 2013-06-18
To give more hints on the ssh option, the remote machine needs to be running the server which is in the package openssh-server for Ubuntu.  For other Linux distros the name might vary a little.  

On the client side you can use your file manager, such as Nautilus.  Press ctrl-L and enter the URI starting with the protocol and ending with the address of the machine.

```

sftp://duckkingman@xx.yy.zz.aa/

```

It's that simple.  Of course you could also use FileZilla or even the text-based [sftp](http://manpages.ubuntu.com/manpages/raring/en/man1/sftp.1.html) client found in the terminal.

The only downside here is that somehow you have to have the OpenSSH server running on the remote machine.

---

### Post by Duckking man on 2013-06-18
Thanks, I think I'll get someone I know well to log into the terminal and get it going since they won't know how to mess up my system even if they wanted to.  I'll be sure to enable ssh at startup on all my new installs from now on so as to avoid this next time.  I'll post this as solved when I can finally get someone at my house to turn it on.

---

### Post by TheFu on 2013-06-18
Don't forget to install **fail2ban** ASAP too.
Chance are that router changes will be necessary for this to work too - at least on the "server-side" of hte network. I suspect this will be the most difficult part of your solution, since someone at the remote location will also need to login to the router, enable port forwarding of the specific from/to port pairs and be comfortable enough to make it all work after a reboot.  The remote machine "needs" a static internal IP address to make this easiest.  Actually, I don't know how to do it without a static IP on the remote machine.

For something so very simple, it does have a bunch of steps.  OTOH, once you get ssh setup once, there really isn't any limit to what can be accomplished remotely.  I've been remotely managing Linux systems for 15 yrs over ssh - I've never seen most of them with my eyes. Heck, my Mom's PC has been remotely managed for 3 yrs now using ssh.  Of course, I physically see that machine a few times every year, but I don't usually do anything special during those visits - the remote methods are good enough - plus I use NX as a remote desktop a few times yearly. NX works over ssh, so it isn't some other funny protocol and is just as secure as ssh (highly secure when keys are used).

Don't forget to setup key-based authentication - ssh-keygen and ssh-copy-id will make your connections easier AND more secure. How great is that?

---

### Post by Lars Noodén on 2013-06-19
+1 for key-based authentication

If you turn off password authentication and use only keys, you can stop worrying about brute force cracking attempts for the most part.

```

PasswordAuthentication no
PermitRootLogin no

```

---

