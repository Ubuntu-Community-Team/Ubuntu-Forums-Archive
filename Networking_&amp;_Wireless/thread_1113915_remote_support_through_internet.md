---
title: "remote support through internet"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by s.dalas on 2009-04-02
Hi everyone,

i need some help and advise here. I want to remote connect through internet to other Os's (for example a friend of mine uses win Vista and sometimes need some support or the same gay using Ubuntu (after my advise!) and doesn't understand something and we talk hours to the phone trying to explain to him the problem). I want to say that i don't need this kind of commands or software for damaging any other system. 

As i trying to find a solution i saw that there are a lot of programs for Windows to Windows and Mac to Mac remote support. Is there something like this for linux to Windows or linux to other Os's??

Do i really need a program for this or can i do it from command line?
i search a little about ssh but i saw that is only for linux to linux ?
then i tried vnc (vncviewer) but when i put the comand i get this 
```
VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:23:14
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Thu Apr  2 13:25:28 2009
 main:        unable to connect to host: Connection timed out (110)

```
then i saw that in vnc site they don't say anything about Vista only Xp and other versions. is this the problem or something else.

Hope to hear some good advises!!!

Thanks in advance!!

---

### Post by superprash2003 on 2009-04-02
you need to have port 5900 open.. which router does that person have

---

### Post by s.dalas on 2009-04-02
the pc i try to connect to is in University so it has static ip but i don't know what kind of router they use if this is what you say.
does it matter anyway ( the kind of router ) ?

So how to activate this port you mention and if i open this with which way (software, command ) do i connect to the other pc? 

I don't know much about this so forgive me if i become tedious :???:

---

### Post by superprash2003 on 2009-04-03
well for this setup to work you need to open port 5900 for which you need access to the router.. but since this is a university network you wouldnt have access to it...

---

### Post by s.dalas on 2009-04-03
thanks a lot for your help. today i made what i want from a windows partition in my system. i will keep searching for doing it through linux. thanks again

---

### Post by superprash2003 on 2009-04-04
check out this program called gitso .. google search it

---

### Post by mocoloco on 2009-04-04
What you want it to connect reverse, either reverse vnc or reverse ssh.  There are lots of VNC clients for windows (ultravnc is a good one), and Mac has it set up natively.

---

### Post by mocoloco on 2009-04-04
Spoke too soon, that's exactly what [gitso]("http://code.google.com/p/gitso/") does, reverse VNC. Thanks superprash2003.  I was planning on doing something like this myself but it's already done!

---

### Post by s.dalas on 2009-04-04
thanks a lot!!!!
gitso sound great because is cross-platform!!! this is what i needed right now! 

thanks a lot again

---

### Post by superprash2003 on 2009-04-05
i needed gitso too , thanks to cybermando for the suggestion  [http://ubuntuforums.org/showthread.php?t=1113241&page=2](http://ubuntuforums.org/showthread.php?t=1113241&page=2)

---

