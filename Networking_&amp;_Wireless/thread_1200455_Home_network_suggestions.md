---
title: "Home network suggestions"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by eddieishavingago on 2009-06-30
Dear forum members. I have four PCs, one with WinXP and three with Ubuntu. I also have two wireless routers and one internet connection. 
What configuration would be best for a home network? What I basically would like is to be able to share folders and a printer between all four computers, but on the other hand I would like it to be safe from internet intruders. 
I would also like to know if it would be necesary (o desirable) to have one PC act as a server, and if so, what options would I have. 
I am not doing business, just doing this for fun, so any atractive suggestions could be entertaining projects to try out.
THANK YOU!

---

### Post by mister_p_1998 on 2009-06-30
I run four Ubuntu PC's and one Ubuntu Laptop on wired and Wifi. I have a Freenas server running on an old 1GHZ Celeron with  500gb storage. All the machines can access this server with read/write access on certain folders. This gives all the users the ability to share files between machines (one machine is a dual-boot XP which can also share the server, although its hardly used on XP any more). One machine has a laser printer on it which is shared with the other PC's. If your internet connection is an ADSL modem router you should be farely safe from intruders, one thing I do with mine is: I have a Wireless extender which allows wifi laptops to connect to the wired network and internet. I have the wireless extender on a timer which comes on at 7.30am, off at 9.00am, back on again at 3.00pm for my sons Xbox games, and finally off for the night at 10.00pm. When Im asleep, there's no wifi available so no one is trying to steal it in the wee hours.
 
Steve

---

### Post by burcyril10 on 2009-06-30
It totally depends what you want to achieve.

If you just want to do some basic file sharing and the like then id just put samba on all the ubuntu's so that windows doesn't get left out and use one of the routers to act as internet gateway - they are usually fine for home security. As for the printer, whack it on one of your ubuntu boxes its fairly easy enough to set it up... even through samba so windows can see and use it.

If you're going to want to setup (external) server apps then perhaps consider using a ubuntu box as a gateway and run everything off that...

---

### Post by eddieishavingago on 2009-06-30
The timer is a great idea, simple and effective. I like it. The thing is I don't want to give up the internet connection at all, and using a timer would cut off my wifi and adsl connection. But as I have two wireless modems I could use one for wireless and the other for internet. I'm not quite sure if that's possible though.
At the moment I have a configuration like what burcyril10 suggests, one router as a gateway and four PCs.
Another configuration inspired by what you guys suggest could be keeping my current configuration, using one wireless router for internet connections, and the other wireless router with a timer for file sharing when I'm at home. I would have two wireless networks.
By the way, samba is needed for sharing between ubuntu and windows, right? Does that mean you can share between ubuntu computers without samba?
Cheers!

---

### Post by jamest09 on 2009-06-30
> **eddieishavingago said:**
> The timer is a great idea, simple and effective. I like it. The thing is I don't want to give up the internet connection at all, and using a timer would cut off my wifi and adsl connection. But as I have two wireless modems I could use one for wireless and the other for internet. I'm not quite sure if that's possible though.
At the moment I have a configuration like what burcyril10 suggests, **one router as a gateway and four PCs**.
Another configuration inspired by what you guys suggest could be keeping my current configuration, using one wireless router for internet connections, and the other wireless router with a timer for file sharing when I'm at home. I would have two wireless networks.
**By the way, samba is needed for sharing between ubuntu and windows, right? Does that mean you can share between ubuntu computers without samba?**
Cheers!

Yes one router and four PCs is the most logical way of doing it.

Yes Samba file sharing between Linux and Windows, for Linux to Linux file sharing you could just use NFS.

---

### Post by mister_p_1998 on 2009-06-30
> **eddieishavingago said:**
> The timer is a great idea, simple and effective. I like it. The thing is I don't want to give up the internet connection at all, and using a timer would cut off my wifi and adsl connection. 

No, you misunderstand me...
only the wifi is on a timer.. the wired connection & router is on 24/7.
Its a wireless EXTENDER it adds a wireless connection to a wired router.
Steve

---

### Post by superprash2003 on 2009-06-30
are both routers wifi? sometimes people club a DSL and a wifi router.. so then both would be required

---

### Post by mister_p_1998 on 2009-06-30
> **superprash2003 said:**
> are both routers wifi? sometimes people club a DSL and a wifi router.. so then both would be required

I have a wired ADSL modem router, and plugged into THAT is a belkin wireless extender.

Steve

---

### Post by eddieishavingago on 2009-07-01
Can samba and nfs be used together on the same machine, or does one imply not having the other?

I have been reading a few tutorials on the web on setting up a samba network, but I have come up with a problem. Apparently I have installed a new version, 3.3 I think, and the tutorials talk about previous versions, so the instructions and options in the tutorials aren't valid for my version. The help in the terminal is too telegraphic for me to understand. Are there any updated tutorials around anybody knows about? Does anybody have an example configuration file I could take a look at?

And regarding NFS, if what I've read is correct, there are two packages that need to be installed: one for the client and one for the server. Can an out of the box ubuntu act as a server? Are there any tutorials for dummies like me? I'm quite new to linux, so NFS is even newer to me.

Thanks!

---

### Post by Iowan on 2009-07-01
[Here]("http://ubuntuforums.org/showthread.php?t=249889") is an NFS How-To (I borrowed the link from **dmizer**'s sig).
There is (somewhat more involved) help page [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

---

### Post by MaindotC on 2009-07-01
> **eddieishavingago said:**
> Dear forum members. I have four PCs, one with WinXP and three with Ubuntu. I also have two wireless routers and one internet connection. 
What configuration would be best for a home network? What I basically would like is to be able to share folders and a printer between all four computers, but on the other hand I would like it to be safe from internet intruders. 
I would also like to know if it would be necesary (o desirable) to have one PC act as a server, and if so, what options would I have. 
I am not doing business, just doing this for fun, so any atractive suggestions could be entertaining projects to try out.
THANK YOU!

You need to specify if you are dual booting and if you are using 8.04 LTS or 8.01 or any of those.

---

