---
title: "Help Me Obi-WAN, you're my only hope."
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by texmorgan on 2009-10-16
Hi,

Here's the problem:

I have a laptop that has either a corrupted file required for the visual login process or hard drive that needs to be replaced.  

It boots up fine until the login screen.

If you try to log in, it seg faults the session, and goes back to the log in screen.

I want to log into the laptop via terminal/ftp/whatever and grab all the files off of that machine I can before I put a new hard drive in it.

Both have Ubuntu 9.04 running on them

server IP: 192.168.0.2
laptop IP: 192.168.0.5

I know there is a way to do this but I can't remember exactly which protocol is used.

Help?

---

### Post by Carl Hamlin on 2009-10-16
> **texmorgan said:**
> 
I want to log into the laptop via terminal/ftp/whatever and grab all the files off of that machine I can before I put a new hard drive in it.

Both have Ubuntu 9.04 running on them

server IP: 192.168.0.2
laptop IP: 192.168.0.5

I know there is a way to do this but I can't remember exactly which protocol is used.

Help?

The key sequence for getting into a terminal is <Ctrl><Alt><F1>. By default, F1-F6 should each have terminal associated with them.

Good luck to you.

---

### Post by benj1 on 2009-10-16
or use a live cd.

ps like the thread title :)

pps you may be thinking of ssh but unless youve installed the ssh-server on it and managed to get it booted properle thats not possible

---

### Post by texmorgan on 2009-10-16
Booting from a live CD gives what I can only describe as a post modern art piece on my screen and is actually worse than booting up with out it.

The <ctrl><alt><f1> got me to the terminal on the wonky laptop!  

But, I'm still not sure how to get the files from my laptop to my server.  I've tried ftp,scp, rcp, etc. but keep getting access denied.  

Is there a port number I should be specifying?

And before you ask, smb segmentation faults too.

---

### Post by texmorgan on 2009-10-16
> **benj1 said:**
> 

pps you may be thinking of ssh but unless youve installed the ssh-server on it and managed to get it booted properle thats not possible

My good man, you've done it.  HUZZAH!

I installed ssh on my server and now I'm taring up my files to send from my laptop.


YOU ROCK!
:guitar:

---

### Post by Carl Hamlin on 2009-10-16
> **texmorgan said:**
> 
The <ctrl><alt><f1> got me to the terminal on the wonky laptop!  

But, I'm still not sure how to get the files from my laptop to my server.  I've tried ftp,scp, rcp, etc. but keep getting access denied.  

Is there a port number I should be specifying?


scp will do the job only if you have ssh server software running on the server. Default port for ssh is 22, but security-minded folks will often change the port. Check the server and see if it's running ssh server software, and if so, what port number you should be connecting on.

---

