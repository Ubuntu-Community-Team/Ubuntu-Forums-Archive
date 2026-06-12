---
title: "Networking Question"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by CosmicFlux on 2009-06-09
Hey,

I have both laptop and desktop systems, both running Jaunty, and would like to use a network cable to create a link between the two. 

What would I have to do to create a network?


Cosmic

---

### Post by reeseslover531 on 2009-06-09
do you not have a router to plug them into? It is much easier if you just plug both into a router.

---

### Post by CosmicFlux on 2009-06-09
I have four LAN ports on the back of my router, so if I were to buy an extra ethernet cable I could just plug them both in and it should just automatically set them up for transfers and communication?

Also, they are both receiving Internet connection from the same router. They communicate wirelessly with the router, could they be set up to communicate in the same way between them?

I'd really like to have them on a file-sharing LAN, but I don't know what hardware I'd require or how to set up the eth0 network. Would I need to know the IP address of both computers?

---

### Post by superprash2003 on 2009-06-09
for file sharing you could use either NFS or SAMBA

---

### Post by puppywhacker on 2009-06-09
if you hook them up directly you will have to assign addresses statically to both like 10.0.0.1 and 10.0.0.2 those are internal addresses you are free to use.

---

### Post by Iowan on 2009-06-09
There's also SSH... I'll include a couple of links, cuz you're gonna need to install a server on one/both machines. The clients are probably already installed. 
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto]("https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto")
[https://help.ubuntu.com/community/SSHFS]("https://help.ubuntu.com/community/SSHFS")
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by CosmicFlux on 2009-06-11
OK, I've installed SAMBA on the machine I wish to use as the server. I've also installed smbfs on the machine acting as the client. The shared folder shows up on the server machine but NOT on the client machine.

I'm not sure how to use the client machine to connect to the server. I don't even know how to resolve the IP address of the server.

Any suggestions?

Bear in mind here my knowledge and understanding of networking is nil, hence this little project. Basically, I just want to be able to connect my two computers together with the Desktop acting as the server, with a share folder containing programs and other files, which the laptop (client) can access. Also, I'm hoping it will give me a little bit of insight into system administration, like creating user accounts etc.


Cosmic

---

### Post by Iowan on 2009-06-11
> **CosmicFlux said:**
> Bear in mind here my knowledge and understanding of networking is nil...Won't be - when you're done ;)
Samba is probably the most complex of the options - after all, it was designed to work with Windows...
From a terminal on each machine, enter **ifconfig** to (hopefully) discover the IP address.  Hopefully, they are in the same subnet (for example 192.168.1.101 and 192.168.1.105). Try to **ping** the other machine. If each machine can **ping** the other, the next step awaits...
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To for the client-side.

---

### Post by CosmicFlux on 2009-06-13
Thanx! That worked, and they ARE both in the same subnet. I got ping responses from each machine to the other, but that was over the Internet using the wlan connections. I'm going to get an Ethernet crossover cable ands try to set up a basic LAN. Will I still need Samba for that?


Cosmic

---

### Post by cariboo on 2009-06-13
If both of your systems are connected through the router and they are both on the same subnet and you are using class c ip addresses 192.168.X.X then you are connecting through the switch built into your router. No need to use a crossover cable.

If you have samba set up properly on the server, open a terminal on your laptop and type:

```
smbclient -L <server> -U%
```

this what I get get when I type the above command:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	images          Disk      mounted iso images
	stuff           Disk      whatever fits
	documents       Disk      documents and such
	music           Disk      tunes
	movies          Disk      Movies and TV
	print$          Disk      Printer Drivers
	HPLaserjet      Printer   laser printer
Domain=[APLUS] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

---

### Post by CosmicFlux on 2009-06-18
Hmm I guess I didn't have Samba set up right then. I've removed the package via apt, think I'll start over and find out where I went wrong first time round.

So basically, to summarize, with both my laptop and desktop system connected through the switch in my router I should be able to network these two computers in a wireless manner?


Cosmic

---

