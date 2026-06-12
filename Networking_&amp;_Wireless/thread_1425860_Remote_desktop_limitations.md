---
title: "Remote desktop limitations"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by c0nfusedami on 2010-03-09
I have just recently got my remote desktop up and running. I would like to leave my ubuntu computer running without a screen so that it will be out of site. I am currently using the computer for printer sharing but would also like to use it for an ftp server and possibly for hosting a web site. My only concern is that I won't be able to set everything up only using the remote desktop, and therefore have to pull out the heavy monitor to do work on it. Does anyone know the limitations of remote desktops if any.

---

### Post by doas777 on 2010-03-09
well, the ubuntu remote desktop requires a user to be interactively logged in, so that is a killer for headless servers. 
I recomend freenx. its easy to set up and use, free, cross platform, is secure (uses ssh tunnels), and performs a good bit better than vnc over mid-low bandwidth links. it also starts it;s own login shell, so you can login if you aren't already.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

the only functionality that it doesn't provide that vnc does, is the abliity for the desktop user to see the remote users session. that is only really useful for training however.

---

### Post by c0nfusedami on 2010-03-09
I'm not terribley concerned about security. My remote use is stricktly on my home network. I'm more concerned with installing different programs. Would this cause me any problems later on?

---

### Post by doas777 on 2010-03-09
> **c0nfusedami said:**
> I'm not terribley concerned about security. My remote use is stricktly on my home network. I'm more concerned with installing different programs. Would this cause me any problems later on?

not quite sure what you are asking. no freenx should not cause any problems installing apps. the security is incedential in your usecase (and mine) but it's nice to know its there in case I ever need to expose nx to the web.

---

### Post by c0nfusedami on 2010-03-09
I just wanted to inquire about any problems that people had with remote desktops to be sure that I'm not going to have to lug out my 30 lb screen again. Thank you for your time I appreciate it.

---

### Post by c0nfusedami on 2010-03-16
Would there be a situation where a computer would sit too long making it impossible to connect to it remotely?

---

### Post by c0nfusedami on 2010-03-16
It appears that my static I.P. settings and my remote desktop settings were reset to the default. could this be caused by the computer resetting or the power outage I incurred?

---

