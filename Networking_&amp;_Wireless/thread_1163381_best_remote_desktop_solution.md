---
title: "best remote desktop solution?"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by scales on 2009-05-18
Hi all. I am fairly good with ubuntu having used it for a few years.  I still go back to xp now and then for a few things.  One thing that I have not quite replaced is logmein.  I use logmein to remotely control my familys computers whenever they need tech support.  I was wondering what would be a good alternative in linux, also thinking about being able to remotely connect to my machine for storage in a secure way.

Lets assume that all the computers will be on dynamic networks so it isnt quite easy to always jump on to the same machine without knowing the ip.  I did a bit of browsing and searching and have come across two solutions.  One is NoMachine NX.  I believe that this is a client just like logmein that allows me to connect to a computer already set up with its server running.  The second would be to register a dns address and vnc through that.

I basically am concerned about security.  Opening a port would make my computers more at risk, but with linux is that still the case?  Anyone have any good opinions on the matter?
Thanks!

---

### Post by pricetech on 2009-05-18
from Windows to Linux, NX is my pick.  From Linux to Windows, RDP works for me just fine.

Security might be a concern over the Internet.  I use NX to remote in to my Linux box here in my office over the Web.  I use fail2ban for security and everything just plain works.  I do have the advantage of a fixed IP here at work, so dynamic DNS is not needed.

All my RDP is internal, so we're not exposed to the web.  VNC might be a better solution since it should allow you to use a non standard port in addition to any security you might use on the computer itself.  TightVNC always worked best for me where VNC is used.

That's my not so short answer.

---

