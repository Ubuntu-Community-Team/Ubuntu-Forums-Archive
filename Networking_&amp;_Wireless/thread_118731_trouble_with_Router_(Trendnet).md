---
title: "trouble with Router (Trendnet)"
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by noob_Lance on 2006-01-17
Hey. all works well i guess you can say... but im setting up a small netowrk and am going to soon put in a server... but with that... i need to be able to access it from outside my network... if im at school i want to be able to SSH and sFTP and remote desktop to it to work on and such. I also have another computer that i wish to be accessable for SSH and FTP only .. i cant figure out how to get my router to work this these services, let alone even get an SSH and sFTP program for windows... if anyone can help me set it up.. it would be appreciated Very much :)

Thank You
~Lance

---

### Post by cwaldbieser on 2006-01-17
[QUOTE=noob_Lance]Hey. all works well i guess you can say... but im setting up a small netowrk and am going to soon put in a server... but with that... i need to be able to access it from outside my network... if im at school i want to be able to SSH and sFTP and remote desktop to it to work on and such. I also have another computer that i wish to be accessable for SSH and FTP only .. i cant figure out how to get my router to work this these services, let alone even get an SSH and sFTP program for windows... if anyone can help me set it up.. it would be appreciated Very much :)

Thank You
~Lance[/QUOTE]

What kind of router do you have (model number)?  On lots of models, you can just HTTP to it's address to get to the administration screen.  You need to forward your SSH port (normally 22, but you might want to change that) to your PC running the SSH server.

As far as an SSH client for Windows goes, PuTTY is pretty reputable in that regard.

---

### Post by noob_Lance on 2006-01-17
ok... well i went to trendnet's site to try and figure out port forwarding... and im hoping i get this right lol... because im not sure wtf im doing haha. and i acutally ment programs to at as the service provider... a friend suggested freessh and freesftp for those... so im going to try them.. and as for model # its tew-431brp

---

