---
title: "n00b needs help setting up LAN"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by lariosa42 on 2010-09-01
Hello.  I've been trying to set up an ethernet connection between my Linux laptop and my wife's Mac laptop for the purpose of ssh-ing and scp-ing.  (She wants me to transfer 50 G worth of files to her computer.)  I've googled around for the last few hours, but I keep finding how-to's like [this one]("http://www.howtogeek.com/howto/ubuntu/setup-openssh-server-on-ubuntu-linux/"), and I need more help than that.

Here's what I've done so far.  On the linux machine, I installed sshd:
```
sudo apt-get install openssh-server openssh-client
```
According to [FONT="Courier New"]ps -Af[/FONT], it looks like [FONT="Courier New"]sshd[/FONT] is running.  
Next, I connected the ethernet cable between the two computers, and on my linux machine, I typed [FONT="Courier New"]ifconfig eth0[/FONT], which gave:

```
[/FONT]
eth0      Link encap:Ethernet  HWaddr 48:5b:39:3d:c3:c2  
          inet addr:24.16.194.245  Bcast:24.16.195.255  Mask:255.255.252.0
          inet6 addr: fe80::4a5b:39ff:fe3d:c3c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:423665201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1204 errors:0 dropped:0 overruns:0 carrier:15
          collisions:0 txqueuelen:1000 
          RX bytes:70234 (70.2 KB)  TX bytes:88264 (88.2 KB)
          Interrupt:37 

```

Now, I don't really know what I'm doing, but many of the guides say to just go to the Mac and type "[FONT="Courier New"]ssh <user-name>@<some-ip-address>[/FONT]."  I can ssh from the Mac to my university's server, for example, so ssh is working on the Mac.  I tried several commands on the Mac:

```

ssh <user-name>@24.16.194.245
ssh <user-name>@24.16.195.255
ssh <user-name>@fe80::4a5b:39ff:fe3d:c3c2

```
(of course changing [FONT="Courier New"]<user-name>[/FONT] to my user name) and I either got "connection refused," or it would just hang, not giving me a prompt.  

Can anyone tell me what I am doing wrong?  Many thanks in advance!

---

### Post by ieee488 on 2010-09-01
If you are connecting PC to PC without a router, you need a crossover network cable not a regular network cable.

---

### Post by lariosa42 on 2010-09-01
OK, that sounds like a pretty major thing I was missing!  I thought I could do it directly with an ethernet cable.  I'll try doing it through my router.

---

### Post by BkkBonanza on 2010-09-01
"Connection Refused" usually means it can talk but could not connect. Check any firewall software and make sure port 22 is open. To be sure sshd is good, use the command **sudo netstat -lntp** and check sshd is in the output and listening on port 22.

Many ethernet ports nowadays can auto-switch the cable pairs so often a crossover cable may not be needed (unlike in the past).

---

### Post by Iowan on 2010-09-01
*Might* need to post the SSH config files. Also, SSH can be picky about permissions.
Not the normal home network-type IP address - both machines are in the same subnet?

---

