---
title: "I think I caused a DOS by port forwarding... oops"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by rootless on 2009-11-19
I need some help ubuntuforums. My roommates are going to crucify me.  I installed openssh-server on my workstation at home. I opened port 22 in my linksys' firewall, and forwarded it to my workstation's static IP.

So far, so good. I spent a few weeks using ssh and sshfs to share files and issue commands remotely- I love it... especially for forwarding xorg sessions.

My roommates 'discovered' that I was running a server and freaked out, claiming that I was making their internet access slow down. Apparently I caused some sort of DOS, although, for the life of me, I can't figure out how.

Is it possible that I cut off their access to certain services that use port 22? Is there any other way I could be messing up our connection? 

I'm going to try to use port 2222 this time... I doubt they need that port, right?

They currently suspect I'm some sort of 1337 4@xx0r who is hacking their intardwebs even though I've tried to explain ssh to them numerous times...

As for the DOS, I suspect that one of them was running a bittorent client.

---

### Post by pricetech on 2009-11-19
I'm reminded of an incident that happened to me a great many years ago.  I moved in to a new house and put up a CB antenna.  Before I could even hook the radio up my neighbors started complaining that I was messing up their tv.

Your roommates are just being paranoid.  I seriously doubt they have even noticed any loss of speed, they just want to complain.

They aren't using port 22 for anything.  It's designated by IANA for SSH.  If you want to move it to an alternate port, for whatever reason, put it above 49152 since those are the dynamic / private ports.

As far as your roommates;  You probably can't do anything to please them, but you do gotta share the place with them.  Good luck with the psychology.

---

### Post by rootless on 2009-11-19
Ahahaha, yeah, machines are obviously my strong point, more than people. 

But hypothetically, if one of them wants to use port 22 in the future, our router is going to send out packets, and then packets will be sent back to 22... but then my IP is going to get them because I told the router to forward to me... right?

Just being careful. Thanks!

---

### Post by pricetech on 2009-11-24
I won't swear to this but I'm pretty sure your computer would just plain ignore them and not respond in any fashion because they wouldn't be initiating a connection.

Port 22 is for SSH.  There's no reason to think your "non hacker" roommates would even consider using it.

---

### Post by rootless on 2009-11-25
Yeah, we'll see what happens.

---

