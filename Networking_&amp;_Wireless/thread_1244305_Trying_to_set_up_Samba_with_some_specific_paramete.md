---
title: "Trying to set up Samba with some specific parameters"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by The Funkbomb on 2009-08-19
Okay, I'll try to keep this as easy as possible.

I have an existing Windows file and printer share set up with 5 computers.  Each has a static IP assigned to it.

.100 is an Ubuntu only laptop.
.101 is a Windows XP only desktop.
.103 is a dual boot between Windows XP and Ubuntu 8.10
.104 is my baby. :)  It's a dual boot between Windows 7 RC and Ubuntu 9.04
.105 is a netbook with XP only.

Don't ask me what happened to .102...

Anyway, all of the windows computers play as nicely as Windows computers can.  I'm trying to get .104 into the file and printer sharing.

Here is the catch though.  I don't want the folder password protected but I want to restrict access only to .101, .105 and the windows boot of .103.  When I get a better understanding of Samba, .100 and the ubuntu boot of .103 will be thrown into the mix.  My router is locked down pretty well but just in case.

I have UFW enabled on all of my Ubuntu computers and they're set to deny all.  On the windows side, I have third party firewalls and they're already configured to let the good times roll.

I just don't know how to set up Samba correctly.  I changed the workgroup name to my workgroup in smb.conf.  Not sure what to do after this.

I tried following this tutorial: [http://www.jonathanmoeller.com/screed/?p=889](http://www.jonathanmoeller.com/screed/?p=889) and temporarily disabled my firewall on .104 but it didn't work.

Can anybody walk me through, step by step?

---

### Post by The Funkbomb on 2009-08-19
Okay, this is how far I got now.

I changed the workgroup name to my workgroup.  Saved it.

I had to add a module to UFW.  Now, on windows I can see my Ubuntu share but I can't see any windows share from Ubuntu.  I can see the workgroup.  I enter the workgroup and the gif spins for 30 seconds and nothing...

What am I doing wrong?

---

### Post by The Funkbomb on 2009-08-19
The plot thickens...

I can access the share from the .101 windows computer.  I cannot access it from the .103 laptop or the .105 netbook.

---

### Post by Bucky Ball on 2009-08-19
Make sure you have ALL the IPs 'allowed' locally on each machine (the ips you want that machine to access that is). If you have a 'deny' list set up anywhere, the machine will ignore anything that is not in the 'allow' list. 

You're certainly getting there though and it sounds like only a matter of time before you make the breakthrough. Sorry can't help more. Played around with Samba but three machine run Ubuntu 95% of the time so using NFS and SSH now (more secure).

---

### Post by superprash2003 on 2009-08-19
you want a certain specific folder to be blocked? or all shared folders from that machine blocked?

---

### Post by The Funkbomb on 2009-08-19
> **Bucky Ball said:**
> Make sure you have ALL the IPs 'allowed' locally on each machine (the ips you want that machine to access that is). If you have a 'deny' list set up anywhere, the machine will ignore anything that is not in the 'allow' list. 

You're certainly getting there though and it sounds like only a matter of time before you make the breakthrough. Sorry can't help more. Played around with Samba but three machine run Ubuntu 95% of the time so using NFS and SSH now (more secure).

I have UFW set up to deny all.  Just the default deny all.

Then I allowed all the local IPs on my UFW firewall.  Since I am the network admin for my home network(scary), all the other computers just allow any connection from this computer.

I'm really puzzled as to why .101 works but .103 and .105 do not.

---

### Post by The Funkbomb on 2009-08-19
> **superprash2003 said:**
> you want a certain specific folder to be blocked? or all shared folders from that machine blocked?

I want one share folder from .104 to be seen by .101, .103, and .105's Windows machines.  If anyone else breaches the network, I want my firewall to block them from seeing the folder.

---

### Post by The Funkbomb on 2009-08-19
News from the front lines!

I got all my windows computers to see my Ubuntu computer.  Now, I just need to figure out why I can't see them...

---

### Post by The Funkbomb on 2009-08-19
Okay, now another twist.  When I add a file from my windows computer into my Ubuntu folder, they are locked.  When I add a file to my Ubuntu computer into my Ubuntu folder, they are locked and Windows cannot edit them.

Weird, right?

---

### Post by The Funkbomb on 2009-08-19
Got my last issue hammered out, I do believe.

Now, the final and original problem.  I cannot open the Windows shares from Ubuntu.  If I get that figured out, without breaking the rest.  Jackpot.

---

### Post by The Funkbomb on 2009-08-19
Problem solved!  It was something about the order of wins in smb.conf and nswitch.conf.  It now works perfectly.

---

### Post by Bucky Ball on 2009-08-19
What did I tell ya! Only a matter of time. Well done and happy filesharing. :)

---

