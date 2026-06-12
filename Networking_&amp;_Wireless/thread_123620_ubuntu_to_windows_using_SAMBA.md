---
title: "ubuntu to windows using SAMBA"
date: 2006-01-30
forum: Networking &amp; Wireless
---

### Post by floyd27 on 2006-01-30
Hello..
I am attempting to access a windows computer (not on a network) through my kubuntu box. 

I have full access to both comps. I would like to be able to get access to the windows files in my Kubuntu system.. I have Ip adress for both and PW's for both systems.
I have been doing some reading and SAMBA seems to be a good way of doing it. However Im having trouble getting started. I dont even know where to find SAMBA on my comp.. It is installed though.
Is SAMBA the right program for doing so? 
I have used sshfs to access ubuntu-ubuntu systems and that works Ok for me.

If anyone can guide me through this or provide a link to a step by step process to this. That would be great.
thanx a bunch..

---

### Post by floyd27 on 2006-01-30
Iv been reading and it seems samab is only for a LAN? Is this correct..?

When it comes to networking im not to great, so I will need to know the little things.. 
Im willing to do the work but im unsre where to start.. 
Is ssh or something else what I should be looking at? 
Just to be clear, I only need to access the windows files through Kubuntu..
I am able to set up a Kubuntu to kubuntu link. But I dont know how to do that for Kubuntu to windows..
thanx again

---

### Post by floyd27 on 2006-01-30
Am I on the right path at least?
Im reading alot but dont even know if im looking for the right thin..

---

### Post by mlomker on 2006-01-31
What do mean when you say that the Windows computer isn't on a network?  How were you planning to connect the two machines?  It's easy to connect from Kubuntu to Windows but I haven't experimented with going the other way.  

[These instructions]("http://www.ubuntuguide.org/#sambaserver") for setting up a Samba server are for Hoary, but I doubt it has changed.

---

### Post by floyd27 on 2006-01-31
What I mean by isnt on a network is, 
the windows comp is at my friends house. With his own internet connection. And my Kubuntu comp is here with my own internet connection..

I am able to access his comp when he is logged into linux, through sshfs. But I what to be able to when he is loggged into windows. 
Ill give that a read and see what I can do..
thanx for that....

---

### Post by Kuprin on 2006-01-31
Actually, from what I've read Windows has released a "security update" eliminating the reading of Samba shares...so you'll never see a Linux share in Windows? I don't know if that's true or not, though it makes some sense to me as a sysadmin, why Micro-shaftyou would do something like that. :p

I've had sharing problems too, however...I'd like to see a better Linux LAN sharing howto...esp for printers. :)

---

### Post by mlomker on 2006-02-01
[QUOTE=floyd27]I am able to access his comp when he is logged into linux, through sshfs. But I what to be able to when he is loggged into windows. 
[/QUOTE]

I see.  You could look around for an SSH server that runs under Windows.  Mapping a Windows share across the Internet would be a dangerous thing for your friend to allow--people are probing for those ports being open and his box would probably get hacked.

---

