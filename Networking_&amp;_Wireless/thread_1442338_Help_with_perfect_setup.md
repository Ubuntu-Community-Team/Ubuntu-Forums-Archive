---
title: "Help with perfect setup"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by A_n_d_y on 2010-03-29
Hi :)

I've played with ubuntu and other distributions on and off for years, ubuntu is the only one I've stuck with as a working system. It works OK for what I use it for but I know it can do more and really work for me but A) I'm scared of playing with it in case I break what already works! B) I'm not sure how to achieve the goal I want.

I'm hoping you guys can help point me in the right direction :)

Setup:
Currently the ubuntu (desktop edition) is running as a basic lamp server, my wife uses this to develop websites without having to upload to the live site. This is working well. Connected to our network via a wireless interface.

Issues:
I've not been able to setup FTP effectively, I would like to be able to FTP files to the local server just as we do the live sites, currently we are simply using file sharing to move files to the web directories on the ubuntu server, this works OK but sometimes permissions or owner need changing after copying involving another step of chmod and chown.

Would like:
1) I would like some peace of mind that I can backup the current setup incase something went wrong, in windows I have system restore, is there something similar in ubuntu? or better? a whole drive image maybe? what are you guys using? recommend?

2) Not important but would be nice to complete the local server by setting up FTP access so it mirrors the live site.

3) This is the big one for me, I would like to be able to use the ubuntu server as a kind of firewall or gateway (not sure of the correct terminology) for an individual untrusted machine. The ubuntu server connects with our network over wireless, I would like to be able to plug a untrusted machine into the wired network port of the ubuntu server so the untrusted machine can access the internet but not see or access our trusted network or any machines on it. I had something set up that almost did this but it broke :(  Ideally I would be able to plug the untrusted machine in and it would obtain a IP and DNS settings automatically from the ubuntu server.

I'm sure this is all very basic, but like I said fearful of messing up a system that is currently working for us so creating a backup is first priority (with easy restore methods!). any advice, tips, pointers, instructions would be very much appreciated

Thanks,
 Andrew :)

---

### Post by Iowan on 2010-03-29
A couple of FTP How-To's for you:
[http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588")
[http://ubuntuforums.org/showthread.php?t=218630]("http://ubuntuforums.org/showthread.php?t=218630")

---

### Post by A_n_d_y on 2010-03-30
Hi Iowan,

Thanks for the links, will see how I go. What are others using as a backup? E.g. like Windows system restore. If I make a mistake and nothing works, what are the options for undo :)

Thanks,
 Andrew

---

### Post by Iowan on 2010-03-30
The Live CD (rescue disk?) lets you go fix many things - forum support should be able to walk you through most "repairs" - or suggest OS re-install (only as a last resort...)

---

