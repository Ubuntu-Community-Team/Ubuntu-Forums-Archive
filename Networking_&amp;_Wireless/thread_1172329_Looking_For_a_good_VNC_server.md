---
title: "Looking For a good VNC server"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by ewendt on 2009-05-28
Ok heres my situation, i need a good reliable VNC server to install on my Ubuntu boxes, i need to be able to configure it fairly well for security purposes such as limiting only a specific IP range and i need it to run at start up not at login. and im also fairly new to Ubuntu so the easier the better. if anyone has any sugestion please let me know. I've tried realvnc and tightvnc servers and can get them to work and no one else seems to have this problem as fa as I'e been able to find i would appreciate some suggestions thanks.

---

### Post by superprash2003 on 2009-05-28
you can combine system->pref->remote desktop and firestarter ( of ufw )

---

### Post by ewendt on 2009-05-28
Well that option is Vino which won't start untill the user logs in, this is unfortunately unacceptable because of the work I and my coworkers need to accomplish with computers that are unmaned on the other side of the plant.

---

### Post by ewendt on 2009-05-29
Hey guys i Actually found some thing recently that i think will work good. Its NXserver from [www.nomachine.com](www.nomachine.com) im still doing some documentation on it but it looks promising and it appears to have all the security i need and functionality as well. im still testing it but will let you all know what i find thanks.

---

### Post by ewendt on 2009-07-02
I found recently durring my cofiguring and testing that NXserver only allows for 2 connecting accounts total. so as soon as you connect with two different accounts to hat server no other account can be givin connection rights. I found FreeNX which is detailed in the Ubuntu web site documentation and now i need to cofigure and test this.

---

### Post by RGPerson on 2009-07-12
How did that work for you?  I want to be able to control my Jaunty box from another computer (Windows, basically).  The Remote Deskop that's in it works....sort of.  I can control the mouse and keyboard, but my display will not update, so if I'm not looking at my TV (which is the monitor for the Jaunty box), I can't see what I'm clicking or typing.  This is hard enough from the couch (works for watching TV, but not for reading text); it will be impossible when I'm in my home office or work office.

I've been trying to install RealVNC (love it in Windows) with no luck. Always says it's missing some shared libraries I have no idea how to get or where to put if I managed to get them.

Never mind. I'm working now. I got rid of Compiz.  It wasn't easy finding out how but I got it and I'm glad it's gone. 

Gabrielle

---

