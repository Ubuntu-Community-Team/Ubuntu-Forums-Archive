---
title: "Remote Desktop as a Service on Ubunto"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by notquiteanewbie on 2009-03-03
I apologize if this has been covered previously. I've tried searching several forums with no luck. 

I am a long time windows users that has been recently converted over to Mac. 

I am running Leopard 10.5.6 as my primary computer and my media computer is running Ubuntu 8.1 all on a local network.

I want to be able to power on the ubuntu computer and log into it via Remote Desktop/VNC. 

Note:
Currently I am only able to do this by first logging into ubunto from that machine then once that session is already started I can remote in from my mac. This is annoying. It should be able to start as a service without me needing to login. 

I am open to any ideas. 

Thank you in advance

---

### Post by dfme on 2009-03-03
hi,
try:
[http://www.nomachine.com/](http://www.nomachine.com/)
good remote desktop application which runs over standard ssh connections using data compression!
so it's fast and secure :D

---

### Post by notquiteanewbie on 2009-03-04
Thank you, do you know if the app is able to run as a service? so I don't have to log in first.

I've gathered so far that this seems to be a limitation of gnome however it appears this is a default setting, as it is considered a security concern, however I'm not sure where it can be changed.

---

### Post by dfme on 2009-03-04
> **notquiteanewbie said:**
> Thank you, do you know if the app is able to run as a service? so I don't have to log in first.

yes... as long as you have an ssh daemon running on your server (or the machine you want to connect to) you can connect via nx machine.
to install ssh daemon (sshd):
```
sudo apt-get install openssh-server
```

nx machine also works with KDE. no limitations

---

### Post by notquiteanewbie on 2009-03-05
Thanks for all the help. 

I followed the instructions...openssh appears to be running now as a daemon (verified in services) but still not working at startup.... 

Nomachine is very fast. I'm not a fan that I can't shutdown or restart the computer via the gui but thats a small trade off. 

Any idea why I still can't connect at startup?

---

### Post by x1101 on 2009-03-05
If security isn't a concern for you, you could just set Gnome up to auto log in (in the options its called timed login). most likely if this no machine requires Gnome at all you would not be able to start it before Gnome is started (and that doesn't happen until you log in, up till then its GDM).

Hope that gives you some thoughts.

---

### Post by dfme on 2009-03-06
> **notquiteanewbie said:**
> Thanks for all the help. 

I followed the instructions...openssh appears to be running now as a daemon (verified in services) but still not working at startup....
hmmm... if you have installed openssh on your ubuntu machine then it should always start running when powering on (without having to logon into a gnome or kde session)
before using nx machine to connect try to connect to your ubuntu machine via ssh. in the console (i think on a mac the console is called terminal) enter
```
ssh username@ip
```
replace username and ip ;)
you should then be asked for a password. if this is the case the ssh daemon is running on your ubuntu machine.

> **notquiteanewbie said:**
> Nomachine is very fast. I'm not a fan that I can't shutdown or restart the computer via the gui but thats a small trade off. 
Any idea why I still can't connect at startup?
another hmmm... i'm able to shutdown or restart the machine remotely using nx machine... otherwise in the console of the ubuntu machine you can enter:
```
sudo shutdown -h now
```
-h shuts the machine down. with -r the machine is restarted.

---

### Post by Sagefrog on 2010-04-19
Independence IT will host your PC-based applications in their data center, purchase and maintain best-in-class technologies and use industry-leading controls.  The Independence IT team handles your day-to-day management, information security, data backup and recovery, and end user connectivity. So you can quickly, efficiently, and affordably create a virtual IT department that rivals those of Fortune 500 companies. Contact Independence IT(client) today - (888) 299-4552  [wwww.independenceit.com]("http://www.independenceit.com")

Hope this helps!

---

