---
title: "networking and ssh question"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by korvirlol on 2009-12-29
I need to get access to my ssh server at home, but of course, before i left for the holidays i forgot to turn port fowarding on the router on. 

Is there a way that you can specify which machine on a lan that this ssh request goes to?

Something like: ssh user@ip:machineIP

Ive gone through the man pages, and the -L switch seems to be the closest thing to what i need, but that requires that the ssh request goes through an ssh server that is to be forwarded to another machine, my situation is that that ssh server is just a machine on the network.

I dont even know if it can be done, but, how can i bypass port forwarding?!

thanks for any help!

---

### Post by iponeverything on 2009-12-29
If you didn't turn on port forwarding and can't log into the router remotely to turn it on, I think that you are out of luck.

---

### Post by Iowan on 2009-12-29
I've been wrong before, but I'm inclined to agree that without port forwarding, it may not be possible to get to the machine. If you can, you should be worried...

I've heard of a process (port knocking?) where the internal machine could make an outgoing connection, but I haven't really studied it

---

### Post by Lars Noodén on 2009-12-29
@ Iowan : Reverse tunnel is the term you are probably looking for.  Port knocking is still the machine listening for a connection, but it only starts listening (or at least only responds) after a specific combination of ports is hit in the right sequence and with the right timing.  There are a variety of ways to do it, including clever [port knocking tricks with iptables](http://www.debian-administration.org/articles/268).  There is even some good(!) Ubuntu documentation on the topic: [Ubuntu Community Documentation: PortKnocking](https://help.ubuntu.com/community/PortKnocking).

However, it won't help right now.  

If the router was configured to forward anything, then that could be used to get in.  

@ korvirlol : this is doable, easily, but may be confusing or stressful the first time.  So treat it like an experiment:

A) If you have a machine with ssh server running that can be reached from your home computer, 

B) and if you have someone you trust with your login information, and who can follow simple computer instructions, 

Then

0) make an account on the external computer
1) send the reliable person the password for the external computer and the password for your account on your home computer by sms or tell them over the phone (not voip).   Then change it ASAP.  

1) have them go to your computer

2) Press *ctrl-alt-f2* to get a login console, this simplifies the instructions.

3) log in using your account

4) log in to your external computer using your account and making a tunnel at the same time

[indent]
ssh -N -f -R 22221:localhost:22 outside.example.org
[/indent]

5) then you log in on the external machine and connect with the ssh client to the local port, using the username for your home machine's account:

[indent]ssh -l korvirlol -p 22221 127.0.0.1[/indent]


---

If you have a permanent external machine, then you can set up a locked-down account that a cron-job on your home machine connects to at certain times to create a reverse tunnel.  You can use keys for authentication.  If you try that please ask for tips so you can learn from some of my mistakes.

---

### Post by DGortze380 on 2009-12-29
Have you tried hitting your IP with a web browser?

It's usually turned off by default, but you may be able to configure your router from the WAN side.

---

### Post by Lars Noodén on 2009-12-31
> **DGortze380 said:**
> Have you tried hitting your IP with a web browser?

It's usually turned off by default, but you may be able to configure your router from the WAN side.

Ick!  I would hope that it is not accessible outside but it is a good reminder that rather than waste time setting up a cronjob to make period reverse tunnels, the smarter way would be to use that first connection (reverse tunnel) to reconfigure the router.  That way subsequent connections can go straight through.  Try to test it from a third box the first time, though, before you log out.

---

