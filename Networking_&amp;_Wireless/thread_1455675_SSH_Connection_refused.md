---
title: "SSH Connection refused?"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by imaginarythomas on 2010-04-16
I'm trying to set up SSH on my work computer (9.10) but I keep getting a "Connection refused" error.

I can connect to myself with 127.0.0.1 no problem but not through my IP.

---

### Post by aeiah on 2010-04-16
make sure the ssh server is running first i guess:
```

sudo /etc/init.d/ssh start

```

if that isnt the problem, is it a firewall issue? ssh uses port 22 by default

can you ping your LAN ip?

---

### Post by imaginarythomas on 2010-04-16
It's up an running.

I'm not sure if it's a firewall issue, how can I check that.

Is my lan IP the same as what I would get from a "what's my ip" site?

---

### Post by imaginarythomas on 2010-04-16
Anyone?

---

### Post by 2hot6ft2 on 2010-04-16
> **imaginarythomas said:**
> 
I'm not sure if it's a firewall issue, how can I check that.
> Firewall, Opening a port

A rule should be added to the servers firewall to allow connections to the servers port. I'm using firestarter, if you're using something else the see the documentation for the one you're using. If using Firestarter open it.
System > Administration > Firestarter

The Staus tab should show it as active
Click on the Policy tab, then left click in the bottom box, then on the + sign.
Here you can enter a Name or use the drop down
Change the port # to the one you setup SSH to use.
And choose who can connect to it. You can choose from Everyone, LAN only, a specific IP Address, or IP Addresses.
You can set it to the IP Address of your client for now (if you want) while configuring things and change it later so you'll be able to connect to it from anywhere.
Click Add, then the Check mark to apply the settings then you can close it.
you can install firestarter like this
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install firestarter
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Then it will be in
System > Administration > Firestarter
> **imaginarythomas said:**
> Is my lan IP the same as what I would get from a "what's my ip" site?
That site tells you your public IP as seen from the Internet.
To find out your computers IP Address
Open a terminal
Applications > Accessories > Terminal
and run
```
ifconfig
```
It will be something like 192.168.1.121 if you're using a router.

See the guide in my sig. below for the SSH, Router and Firewall parts.

---

### Post by imaginarythomas on 2010-04-16
I'm trying to connect from outside my work network (from home) so the 192.168.x.x ip address won't have the same meaning there.

the SSH is set up and running but what ip address do I use to connect from outside this network?

---

### Post by 2hot6ft2 on 2010-04-16
> **imaginarythomas said:**
> I'm trying to connect from outside my work network (from home) so the 192.168.x.x ip address won't have the same meaning there.

the SSH is set up and running but what ip address do I use to connect from outside this network?
You would use the public IP Address to connect from outside the LAN.
You need to do a Port Forward to the server in your router if you have a router so the connection is sent to that computer. It's all in the guide.
See the section
**Static IP Address for the server & port forwarding**

---

### Post by imaginarythomas on 2010-04-16
Okay, I'll read it more carefully, thanks!

---

### Post by 2hot6ft2 on 2010-04-16
> **imaginarythomas said:**
> Okay, I'll read it more carefully, thanks!
You're welcome. I think it will answer most if not all your questions and some you don't even know to ask yet.

---

