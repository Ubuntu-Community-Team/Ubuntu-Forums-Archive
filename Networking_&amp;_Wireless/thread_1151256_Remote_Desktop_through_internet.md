---
title: "Remote Desktop through internet?"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by phantom3113 on 2009-05-06
A friend of mine recently put Xubuntu 9.04 onto his desktop and I've been helping him set it up and such. However, showing him how to do things would be easier than trying to describe them to him and I don't feel like having to drive over to his house all the time. I was looking into the Remote Desktop thing, but could only find howto's on doing it through a local network and/or on a server. My question is, can this be done through the internet and if so, how?

---

### Post by mattgyver83 on 2009-05-08
The answer is yes, however depending on the router and system it can be easy, to fairly difficult to setup.

Remote Desktop Viewer which is already on ubuntu can connect to VNC servers.  In order to do this you will have to have him download some sort of vnc server software (i prefer tightvnc but there are a few) and install it on his computer.  As well he will have to open up ports on his routers (and possibly firewall also) for you to connect to, and forward those ports to the correct IP address on his network if he has more than one computer.

You will also need a package called x11vnc you will need to configure, which will let you connect to his "actual screen" seeing as he is on linux, otherwise you will just connect to a new x session run in the background.  The xsession is okay if you want to just do some cli work, but then your not really showing him are you but will allow you to work in the background while he fiddles around.

From there its as easy as calling him up and telling him to start the vnc server, and then Remote Desktop Viewer can connect by pointing to his IP : port/password and you can access his desktop for him remotely.

If he has just a few computers, and a decent brand router this will be a snap.  If he has several on a network and his router is an off brand.... well, you know.

hope that answered some of your questions.

---

### Post by phantom3113 on 2009-05-11
He's just using one computer, his desktop that he installed Xubuntu on. I'm not sure what router he uses, but I can find out. I'll look into the x11vnc package and tightvnc as well and see if I can get anything going with those. Thanks for the reply!

---

