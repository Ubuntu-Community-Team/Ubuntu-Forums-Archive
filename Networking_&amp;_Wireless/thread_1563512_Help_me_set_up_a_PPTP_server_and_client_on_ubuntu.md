---
title: "Help me set up a PPTP server and client on ubuntu"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Disabled20240622 on 2010-08-29
OK, so I have 2 ubuntu machines, a laptop on 10.04 and a desktop on 10.04 server. I want to put a VPN server on the server and a VPN client on the laptop.

The laptop should connect to the server from the same subnet and from other subnets. The idea being that I can un-dock the laptop (go wireless) and make it look like my IP address never changed so that my SSH sessions don't need to be restarted.

I want to use PPTP because Ubuntu has a built in client. As for the server, I've tried every guide out there and I just cannot get the client to connect to the server.

Here's some information about the machines:

[INDENT]tomg the server has static IP 50.20.163.35 on subnet 50.20.163.0 /24.

alan-laptop the client has a dhcp address on the 50.20.163.0 /24 subnet, and on many other subnets starting with 50.[/INDENT]

What do I actually need to do to configure this server, and what settings do I need to use on the client?




(50.20.*.* is not my real address block, I don't want to reveal the organisations name, I will transplant the real numbers in to your replies).

---

### Post by dmizer on 2010-08-29
I do not know anything about PPTP VPN, and many people here probably won't. Ubuntu also has an OpenVPN client by default, and there are more people here who have experience with OpenVPN.

Is there some reason you prefer PPTP over OpenVPN?
> **BigglesPiP said:**
> The laptop should connect to the server from the same subnet and from other subnets. The idea being that I can un-dock the laptop (go wireless) and make it look like my IP address never changed so that my SSH sessions don't need to be restarted.
I don't really think that VPN will do what you want to do. You should investigate the "screen" utility. The "screen" utility will keep any ssh session live and allow you to disconnect and reconnect whenever you like.

Screen howto: [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by Disabled20240622 on 2010-08-31
Most of the ssh sessions I ave open have a screen session at the end already, but I still have to re-start the ssh session, it does not solve the problem, plus screen not a nice terminal to use it's just a neat way to keep a script going if I go away.

I'd happily use OpenVPN, I've also tried following many guides, but was never able to get the server to start.

---

### Post by dmizer on 2010-08-31
I still think you are looking for something that can not really be done. Any time you switch internet gateways, from wired to wireless or vice versa, you necessarily sever everything that had been passing through that connection, including VPN traffic. You cannot switch from wired to wireless without severing every connection, including VPN, and reestablishing everything wirelessly.

If your computer is mobile and switches access points, I know of no way to keep any kind of sesson, ssh or otherwise, alive while changing those access points.

Perhaps I am not completely understanding your needs, but it does not look possible to me.

---

### Post by Disabled20240622 on 2010-08-31
Currently:

[INDENT]ssh to loads of machines
go wireless
ssh sessions are broken because my IP changed
killall ssh
start them again as I use them[/INDENT]

What I'm thinking:

[INDENT]sign in to vpn
ssh to loads of machines
go wireless
vpn and ssh sessions are all broken
sign in to vpn again
ssh sessions continue, as my "external IP" remained the same[/INDENT]

Can a VPN work like this?

---

### Post by dmizer on 2010-08-31
VPN and SSH sessions are broken because your path to the internet was severed. If you change from wired to wireless, your connection to the internet is severed and you will have to reestablish both your VPN **and** your SSH sessions.

I think what you need is a third machine.

laptop -> desktop with permanent internet connection -> gateway --------> lots of machines.

Where->
laptop has one ssh session connected to the desktop
desktop has multiple ssh screen sessions to many machines

This way, you can switch your laptop from wired to wireless, SSH into your desktop and continue on as if your connection never changed. This is what I do.

```
dmizer@japan:~$ screen -list
There are screens on:
	3964.win7	(08/29/2010 08:57:44 PM)	(Detached)
	650.lucid	(08/27/2010 10:39:17 PM)	(Detached)
	5366.dmizer-os	(08/22/2010 10:38:03 PM)	(Detached)
	5307.xubuntu	(08/22/2010 10:37:06 PM)	(Detached)
	5257.xmpp	(08/22/2010 10:36:37 PM)	(Detached)
	5209.www	(08/22/2010 10:35:26 PM)	(Detached)
	5052.gateway	(08/22/2010 10:31:41 PM)	(Detached)
7 Sockets in /var/run/screen/S-dmizer.

```
In each of those is an SSH session to a different machine. I can SSH from anywhere, and from any machine and reattach to any of those SSH sessions.

---

### Post by Disabled20240622 on 2010-09-01
Sorry, that's wrong, you can sever your connection all you want with SSH, so long as you come back on the same IP address (from the server's perspective) the sessions *will* restore on their own the next time you send a character, no matter how many packets were lost and no matter how long (there is no timeout), ssh is *very* robust.



I would rather have to restart 25 ssh sessions than use screen, I only use it where I'm running a long script or recording a terminal.

---

