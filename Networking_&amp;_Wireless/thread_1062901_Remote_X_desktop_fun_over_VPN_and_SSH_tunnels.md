---
title: "Remote X desktop fun over VPN and SSH tunnels"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by Pierre-Étienne Messier on 2009-02-07
Hello,

Where I work, we have a VPN access to be able to join the network from anywhere, from my home for example. This works great, except that currently the VPN client is Windows only. Therefore, I can't use it (directly) from my Kubuntu laptop.

First, let me introduce a graphical representation of the network topology between my home and my machine at work:

[IMG]http://pemessier.hexpresso.org/Job.png[/IMG]

As you can see, I have 2 machines at home, a Kubuntu laptop (my main machine) and an old WinXP machine. I am behind a Linksys router, which is configured to redirect port 22 (SSH) to my laptop so that I can connect to it from the outside (this works).

At work, I have a WinXP machine which contains a Linux virtual machine running in VMWare (on the same machine, but they have 2 different IPs).

Currently, I am able to develop on my Work WinXP machine from my Home Linux laptop fairly easily. First, I use Krdc to login to my home WinXP machine (RDP is pretty fast and works great -- I have better performance using RDP than VNC). Then, I connect the WinXP machine to the VPN. Once connected, I open a RDP session on my Work WinXP machine. Even with 2 nested RDP sessions, performance is quite good on the WinXP machine at work, as seen from my Linux laptop.

But, when I need to develop in my Linux VM from home, this is where it gets tricky. For an unknown reason, the performance of the VM display over remote desktop is just awful (but it's very good when I am using it locally). Even if I use VNC directly to the VM from my home WinXP machine (that is, without opening a second RDP session), it's just not good at all to be somewhat productive.

I have tried 2 things recently. First, I installed XMing (free X server for Windows) on my Work WinXP machine. I created a SSH tunnel to my VM from there, and launch GUI apps on the XMing X server ('xcalc -display 192.168.2xx.15:0' for example). The performance is great locally, and it's still quite good over nested RDP sessions.

The second thing I tried, is to create a SSH tunnel between my Kubuntu machine and my VMWare machine at work from my Home WinXP machine. For example, using Putty on my home Windows machine, I connect to my laptop and creates a tunnel on port 2222 to the remote machine 192.168.2xx.78:22. Then, from my Linux laptop, I ssh to localhost:2222 which logins to my remote VMware machine. From there, performance is excellent (well, it's just text in a console on SSH!).

These 2 experiments leads me to wonder if there should be a way to combine these 2 methods, but re-use the running X Server on my Linux Home laptop to display the programs launched on my Linux VMWare machine at work. This is currently where I am confused. Keep in mind that I can ssh from my Linux VMWare machine to my home Linux laptop directly if needed.

I hope everything's clear, I know it's quite complicated ;)

Thanks!

---

### Post by graysky on 2009-02-07
[Parallel vnc servers on LINUX](http://knoppmyth.net/phpBB2/viewtopic.php?t=19428)
[Securing via ssh tunnels](http://knoppmyth.net/phpBB2/viewtopic.php?t=19211)

---

### Post by Pierre-Étienne Messier on 2009-02-10
Ok I got it to work the way I wanted!

After creating the tunnel between my Linux laptop and my Linux VM (through my WinXP home pc), I had to set the "DISPLAY" environment variable to ":10.0" to make it work. Works great (even glxgears), but way too slow :(

I am considering NX now (just heard about it yesterday), I tried it just a few seconds but I couldn't manage to setup it right. I'll look into this in the next few days...

Thanks!

---

