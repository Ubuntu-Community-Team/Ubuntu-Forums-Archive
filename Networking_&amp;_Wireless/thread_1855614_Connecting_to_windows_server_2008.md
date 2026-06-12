---
title: "Connecting to windows server 2008"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by jetsonic on 2011-10-06
Hi all.

I can't connect to the server at my work, with my linux pc at home. I am using remmina which should support rdp. What can I be doing wrong? I am able to connect if I am at work, connecting to their wireless network.

Do I need to install additional plugins? Or is there no software yet able to perform this action?

---

### Post by collisionystm on 2011-10-06
> **jetsonic said:**
> Hi all.

I can't connect to the server at my work, with my linux pc at home. I am using remmina which should support rdp. What can I be doing wrong? I am able to connect if I am at work, connecting to their wireless network.

Do I need to install additional plugins? Or is there no software yet able to perform this action?

Do they have an RDP port opened up to the world? Are you using a VPN? Your not trying to connect with a local IP on a non-vpn network are you?

---

### Post by jonnyboysmithy on 2011-10-06
Try using samba instead, I don't know that much about it but after a quick google it seems thats the way to go.

[http://lmgtfy.com/?q=connecting+to+windows+server+from+linux](http://lmgtfy.com/?q=connecting+to+windows+server+from+linux) :)

---

### Post by jetsonic on 2011-10-06
They do have a port opened, as I am able to connect when using windows 7. I am not using a vpn. I am connecting to server name "rd.<name>.dk

---

### Post by collisionystm on 2011-10-06
> **jonnyboysmithy said:**
> Try using samba instead, I don't know that much about it but after a quick google it seems thats the way to go.

[http://lmgtfy.com/?q=connecting+to+windows+server+from+linux](http://lmgtfy.com/?q=connecting+to+windows+server+from+linux) :)

Samba wont work lol.

He just wants to remote desktop. And yes, Remmina does work. It is one of the best programs out there. Make sure you put it in console mode if you want to access the box on Terminal 0.

---

### Post by jetsonic on 2011-10-06
lol, I did google quite a lot mate.

---

### Post by jetsonic on 2011-10-06
> **collisionystm said:**
> Samba wont work lol.

He just wants to remote desktop. And yes, Remmina does work. It is one of the best programs out there. Make sure you put it in console mode if you want to access the box on Terminal 0.

Not sure what you mean with console mode and terminal 0, sry

---

### Post by collisionystm on 2011-10-06
Hmm....

Is your Windows 7 laptop on their domain?

---

### Post by jetsonic on 2011-10-06
No my win 7 comp is connecting from my home network...

---

### Post by collisionystm on 2011-10-06
> **jetsonic said:**
> Not sure what you mean with console mode and terminal 0, sry

A terminal is split into different 'levels' so to speak. Everytime you remote desktop, the server will give you a new terminal number to remote onto.

When you remote desktop using console mode, it takes you onto terminal 0 which is the same desktop you would see if you were in front of the computer itself.

---

### Post by jetsonic on 2011-10-06
Ok. So how will I put in console mode?

---

### Post by collisionystm on 2011-10-06
> **jetsonic said:**
> No my win 7 comp is connecting from my home network...

Try pinging the dns address of your server 2008 and then remote to the ip address instead of the name

---

### Post by collisionystm on 2011-10-06
> **jetsonic said:**
> Ok. So how will I put in console mode?

In remmina, look through your options when you open a new rdp connection, you will see 'Attach to console' windows 2003 and later

---

### Post by jetsonic on 2011-10-06
Connecting to IP-address fails aswell.

---

### Post by collisionystm on 2011-10-06
on Windows 7

Go to Start, Run

type mstsc /admin

That will put you into console

If you dont have run on your start menu, just search RUN in the box on the start menu, and it will pop up

---

### Post by collisionystm on 2011-10-06
Do you have a firewall enabled?

---

### Post by jetsonic on 2011-10-06
firewall is disabled on my linux pc.

---

### Post by collisionystm on 2011-10-06
Weird. So you can ping the address of the server from your linux box. You installed remmina. You open remmina, new connection, choose RDP and under hostname you put the address of the server 2008. When you hit connect it just says failed? strange.....

---

### Post by jetsonic on 2011-10-06
Well, that's about it. It hangs for a couple of minutes while attempting to connect though...

---

### Post by collisionystm on 2011-10-06
Well, try installing KRDC and see if that works. Maybe it is a problem with remmina? Although I do not understand why

---

### Post by jetsonic on 2011-10-06
Would adding port do anything? Don't know which one though. I would suspect the server, if only I wasn't able to connect with my win 7 comp..

---

### Post by collisionystm on 2011-10-06
No adding the port wouldn't do anything unless it was different than 3389. That is the default RDP port...

I wonder if there is some kind of security on the server 2008 that only allows a windows version of rdp to connect. Let me check my box

---

### Post by collisionystm on 2011-10-06
Question,

While you are trying to connect with your Linux box, are you already connected with your Windows 7 machine? I ask because if you do not have Terminal Server licences I belive you can only have 2 rdp sessions. One on terminal 0 and the other on terminal 1.

---

### Post by jetsonic on 2011-10-06
nope, because my win 7 is one of the dualboots on the machine :-)

---

### Post by jetsonic on 2011-10-06
KRDC leaves me hanging aswell...blue screen in console mode...nothing else. Asks for my login name and password, but nothing happens.

---

### Post by collisionystm on 2011-10-06
> **jetsonic said:**
> nope, because my win 7 is one of the dualboots on the machine :-)

Who built the server?

I was just reading this

> When using Windows Server 2008 Terminal Server, consider using TS Gateway - Using the new capabilities of Microsoft Windows Server 2008 TS Gateway provides further protection of RDP traffic by encapsulating it into SSL packets – much like SSL VPN, but without the need to deploy special VPN servers. The benefit of using the TS Gateway capabilities of Microsoft Windows Server 2008 is that remote users will only be granted access to the internal servers based upon a strict policy that can be enforced on the TS Gateway, and when combined with the NAP capabilities of the system, will only allow connection of computers that fully meet the security requirements set by the administrator.

Remmina may fail to meet a security requirement. Try another rdp program.

---

### Post by jetsonic on 2011-10-06
Well, I've read about TS gateway aswell, and I'd have to ask the guys working on the server. I've tried several rdp programs, and it's all the same, so I guess I'll have to wait a while before going all out linux on my work...

Thanks a lot thought anyway.

---

### Post by collisionystm on 2011-10-06
> **jetsonic said:**
> Well, I've read about TS gateway aswell, and I'd have to ask the guys working on the server. I've tried several rdp programs, and it's all the same, so I guess I'll have to wait a while before going all out linux on my work...

Thanks a lot thought anyway.

Yup... no problem!

I guess you could always run a virtual Windows  on your computer? But that would absolutely defeat the purpose of what we are doing here.

Good luck, I hope you find your answer

---

### Post by jetsonic on 2011-10-06
lol, I did try that aswell, but wine keeps messing up some language packs...and yeah, I agree. I'd prefer another way. 

Later...

---

### Post by dcstar on 2011-10-07
> **jetsonic said:**
> Hi all.

I can't connect to the server at my work, with my linux pc at home. I am using remmina which should support rdp. What can I be doing wrong? I am able to connect if I am at work, connecting to their wireless network.

Do I need to install additional plugins? Or is there no software yet able to perform this action?

Unless you **know** that you are using the correct ports etc. **and** a Windows PC can connect successfully, you probably do not have external access.

Most sane organisation do not allow direct access to a server's RDP port from the Internet (the security risk is far too high), they require a VPN connection into the network. Ask your System Administrator how to do it.

---

### Post by saintslaughter on 2012-03-08
I have this exact same problem with Remmina, KRDC, and RDViewer. ALL settings are correct. And using a windows machine works flawlessly. Its not the firewall on any router or computer. And it is not some policy setting on the server, they are using 2003. Reinstallation of my client software is useless as well.  Its a shame this couldn't be resolved.

---

### Post by pybe on 2012-10-23
Been looking for a solution to this as well, only thing I can find is some software for $20 [http://itap-mobile.com/desktop/rdp](http://itap-mobile.com/desktop/rdp)

They have a free trial which I must say works well.

Might just end up dropping the cash.

---

