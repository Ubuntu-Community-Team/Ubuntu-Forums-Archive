---
title: "Any really detailed tutorials for ssh?"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by zer010 on 2011-01-10
I've been wanting to set up an ssh server on my home network, but I can't seem to find any really detailed, definitive tutorials on how to set it up and use it.  One question I always have is, "How does this work when the network is wired through a router."  How does a router affect how I will use ssh? If I'm out and about, how can I ssh into my PC at home to get to my files and such?  
Currently, I'm in the process of setting up an old test PC so I have something to ssh to and practice with.

---

### Post by AVanover5 on 2011-01-10
First, open up terminal and install your (OpenSSH) client and server with the following command:
```
sudo apt-get install openssh-server openssh-client
```
Your server is ready by default. You can test it with either of these commands (change the italicized accordingly):
```

ssh localhost
ssh *user@ip-address*

```
Start, stop, and restart the server.
```

sudo /etc/init.d/ssh start
sudo /etc/init.d/ssh stop
sudo /etc/init.d/ssh restart

```

I'm sure you can find documentation about OpenSSH on their site if you'd like detailed information. What information do you want  specifically? Key generation maybe? For your other question about how it works through the router: I recommend taking a network engineering course online. Here is a real simple generalized one: [http://www.youtube.com/watch?v=TVvEheZVwdg](http://www.youtube.com/watch?v=TVvEheZVwdg)

---

### Post by pricetech on 2011-01-10
To answer the part about accessing from elsewhere, you'll need to set up port forwarding in your router and you'll probably need a dynamic DNS service to resolve your IP for you.

I can't be more specific since I'm not in front of your router, but you should be able to find it in your router's setup somewhere.

You'll need to either give your "server" a fixed IP or reserve one for it in your router.  I prefer the second option, but again the details are specific to your particular router.

If you decide you need a GUI, I recommend NX from nomachine dot com.

---

### Post by zer010 on 2011-01-10
Thanks for the help so far, I'm still relatively new with some of the networking operations.  I'm including a screenshot of an area of my router's settings. I'm assuming that this is where I configure port forwarding, correct?

---

### Post by perspectoff on 2011-01-10
[Redacted. Server error]

---

### Post by perspectoff on 2011-01-10
[Redacted. Server error].

---

### Post by perspectoff on 2011-01-10
[Redacted. Server error].

---

### Post by perspectoff on 2011-01-10
Full SSH guide.

Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#SSH](http://ubuntuguide.org/wiki/Ubuntu:Maverick#SSH)

or

Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#SSH](http://kubuntuguide.org/Maverick#SSH)

---

### Post by zer010 on 2011-01-10
First, thanks for the link. I had not seen that one before and it actually references the use of a router. 
Now, is there a reason for the multiple posts?

---

### Post by perspectoff on 2011-01-10
[Redacted. Server error].

---

### Post by perspectoff on 2011-01-10
> **zer010 said:**
> 
Now, is there a reason for the multiple posts?

Yeah, the Ubuntu Forums server has been squirrelly lately. I post once and several copies show up.

---

### Post by perspectoff on 2011-01-10
> **zer010 said:**
> Thanks for the help so far, I'm still relatively new with some of the networking operations.  I'm including a screenshot of an area of my router's settings. I'm assuming that this is where I configure port forwarding, correct?

By default SSH is on port 22 (although you can set it to any port you'd like in the OpenSSH configuration file. For example, I use port 22222.)

The router must be set to forward the port you choose to the computer on the LAN that is the SSH server.

So, for example, assuming you kept the default port 22 for SSH, and your SSH server is at 192.168.0.56 and is listening on port 22, then the router must be set to forward all port 22 traffic to IP 192.168.0.56.

That's all you have to do with the router.

So, in your Belkin router, on line 1 under LAN IP Address, enter the IP of your computer on the LAN (e.g. 192.168.0.56, or whatever it is. If you don't know, use ifconfig in a command line terminal).

Then leave it at TCP and for both the LAN port and public port enter 22. Make sure you tick the enable box, and Set it.

---

### Post by zer010 on 2011-01-10
> **perspectoff said:**
> By default SSH is on port 22 (although you can set it to any port you'd like in the OpenSSH configuration file. For example, I use port 22222.)

The router must be set to forward the port you choose to the computer on the LAN that is the SSH server.

So, for example, assuming you kept the default port 22 for SSH, and your SSH server is at 192.168.0.56 and is listening on port 22, then the router must be set to forward all port 22 traffic to IP 192.168.0.56.

That's all you have to do with the router.

So, in your Belkin router, on line 1 under LAN IP Address, enter the IP of your computer on the LAN (e.g. 192.168.0.56, or whatever it is. If you don't know, use ifconfig in a command line terminal).

Then leave it at TCP and for both the LAN port and public port enter 22. Make sure you tick the enable box, and Set it.
Thank you so much! That makes so much sense! If you had the time, you  ought to write tutorials.  Now, does this also apply to intranetwork  connections or only incomming external connections?  
I've tried to run ssh once, but couldn't connect within my network. I  figured it might have something to do with having a router. That's been a  while back and lately I've decided that I really should learn how to do  this.

---

### Post by zer010 on 2011-01-10
Well, unfortunately, I can't test anything right now because I'm having some hardware issues. When I get my other PC up and running, I'll start trying everything out and I'll let y'all know how much success I have or ask more questions if I run into any problems.

---

### Post by zer010 on 2011-02-09
Ok, I finally got my test box up and running!  It's nothing more than a Ubuntu 10.04 CLI install with openssh-server and a few other(non-relevant) things installed.  If I configured sshd_config properly, I should be all set.  Now I just tried to access it with the IP address that it is assigned and the client came back with "No route to host".  Although, I'm now thinking that I still need to set up port forwarding from the standard "22" to what I specified in sshd_config.

---

### Post by zer010 on 2011-02-10
Ok, I think I made some progress....:\   It didn't give me the "no route" routine, but gave me a "connection timed out".  YAY!.......i guess......

---

### Post by zer010 on 2011-02-10
Ok, a little more "progress"..... I accidentally switched some numbers in the IP address, but I fixed it and now I'm just getting "Connection refused'......hmmmmm....... 
Edit: I'm trying just about everything under man ssh and I am just not getting what I'm doing wrong. 
Either my server file isn't setup properly or I'm messing up when trying to connect.....

---

