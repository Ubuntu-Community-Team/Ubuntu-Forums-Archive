---
title: "SSH error password incorrect"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by 1nooodlse on 2009-09-23
I am having trouble logging into my ssh

It works fine if I use:
"ssh kidney@kidney-ubuntu"
"ssh localhost"
"ssh -l kidney@kidney-ubuntu"
"ssh [email]kidney@192.168.1.my[/email]-computer"

but if I get this error using my external ip:

kidney@kidney-ubuntu:~$ ssh [email]kidney@my.external.ip.here[/email]
DD-WRT v23 SP2 std (c) 2006 NewMedia-NET GmbH
Release: 09/15/06 (SVN revision: 3932)
kidney@71.92.165.177's password: 
Permission denied, please try again.
kidney@71.92.165.177's password: 
Permission denied, please try again.
kidney@71.92.165.177's password: 
Permission denied (publickey,password)

I have found similar problems elsewhere in the forums but none of them have worked

---

### Post by robert_pectol on 2009-09-23
Here's a clue:
> DD-WRT v23 SP2 std (c) 2006 NewMedia-NET GmbH
Release: 09/15/06 (SVN revision: 3932)
Your router, running DD-WRT, is intercepting the SSH connection so you are inadvertently attempting to login to your router, not your box.  The appropriate port forwarding will resolve your issue.

Robert

---

### Post by 1nooodlse on 2009-09-23
I forwarded the port on my router but i am still getting the error i think i need to contact my isp

---

### Post by robert_pectol on 2009-09-23
Disable the SSH server in your DD-WRT router or change the port on which it listens and it'll probably work.

Robert

---

### Post by 1nooodlse on 2009-09-23
i think that router is for my isp they block all of the port there, i may be wrong but i don't think there is an ssh server on a linksys wrt54gs router

thanks for your help i think i can fix the problem now

---

### Post by robert_pectol on 2009-09-23
My guess is that the WRT54Gs **IS** the DD-WRT router.  DD-WRT is a third-party firmware designed to replace the standard Linksys firmware on many of their routers.  It's open-source and Linux based.  Your WRT54Gs is probably running DD-WRT.  Did your ISP provide that router for you?  It seems a bit odd that you would be running DD-WRT without knowing it, especially if it is your own router and not something they provided.  Maybe they did though.  At any rate, it is obvious that when you attempt to establish an SSH connection from outside, a router running DD-WRT is intercepting it.  Whether it's your box or theirs, that's what is happening.  Good luck.

Robert

---

### Post by 1nooodlse on 2009-09-23
my router has the original firmware i think i am behind another gateway from my isp. It says it's a servgate point force managment console everything but the front page is locked. I'll just contact my isp and see what i can do.

---

