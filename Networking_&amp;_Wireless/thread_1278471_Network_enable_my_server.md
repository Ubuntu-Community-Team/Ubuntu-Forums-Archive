---
title: "Network enable my server"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by Brouschin on 2009-09-29
I'm a newbie who is trying to make a switch to Ubuntu. I have installed Ubuntu on my PC and am trying to make it accessable over the network/internet. Can someone please guide me as to how I can access my Server over the internet from other PCs. 
 
I've tried to find stuff from the internet but I have been unsuccessful
 
Any help will be greatly appriciated.
 
Thank,
Brouschin

---

### Post by Hospadar on 2009-09-29
Depends on how you want to get access.  There are many methods, which tend to be pretty different both in style and in actual technologies than in the windows world.

Probably the most well known is ssh, it allows you to get a very secure shell on a remote system an run any program (including graphical applications) from the remote system.

Look up ssh and X11 forwarding on the google-tron, describing everything you can do with these is a little beyond the scope of a forum post.

There are other options like vnc for remote-desktop type access, but ssh will be faster and more secure and generally more elegant and usable.  ssh will also allow you to conveniently share files with almost any ftp client (filezilla for example).  The only turn off for some people with ssh is that it provides terminal access, from which you must launch whatever programs you want, which honestly isn't a big deal, but if you've never done anything on a command line, it can be a little daunting at first.

Anywho, my vote for remote access is ssh, it's fast, powerful, and secure.  If you aren't comfortable on a command line, just google "linux command line tutorial" and you'll find all sorts of useful info.

---

### Post by Iowan on 2009-09-29
How do you connect to Internet - router?  You will probably need to enable port-forwarding.  Which ports depends on the protocol...

---

