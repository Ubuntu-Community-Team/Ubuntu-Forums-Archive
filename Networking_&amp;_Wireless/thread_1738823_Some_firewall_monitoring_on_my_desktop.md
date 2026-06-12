---
title: "Some firewall monitoring on my desktop?"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by azzid on 2011-04-25
Hi,

I quite recently installed ubuntu 10.04 server on a piece of hardware that is like 10 years old. Needless to say computing power is rather scarce, but ubuntu is actually living quite well on 128mb of memory. I see a slight lag logging in with ssh, but all in all the machine is behaving good. I use it as a firewall, and since my internet is only 10 mbit the machine is powerful enough.

Given the limitations of the machine though I am a bit scared that it will sooner or later get overloaded and degrade my internet connection. Therefore I'd like to monitor the machine to see if cpu/memory/network spikes. I'd like to see theese graphs on my desktop (also ubuntu 10.04), much as I do for my local machine, but I don't even know where to start looking for such functionality.

Anyone got some tips?

---

### Post by collisionystm on 2011-04-25
Use Zentyal. Everything you need and runs on 10.04. ONLY 10.04 so lucky you. You can either download the ISO from their site and do a fresh install or add the PPA. If I were you I would do the fresh install. SO EASY TO CONFIGURE. You will be up and running in a 1/4 of the time it took you to setup ubuntu server.

[http://www.zentyal.com/](http://www.zentyal.com/)

It is all managed through a web interface. You will see Graphs etc... and lots of pretty colors =)

---

### Post by azzid on 2011-04-25
wow, thanks for the quick reply collisionystm!

Zentyal seems cool, but it's a bit more than what I had in mind here.

I was thinking more along the lines of the System Monitor plugin for the gnome panels.

---

### Post by collisionystm on 2011-04-25
if you are using server why are you running a GUI?? You might as well just install Ubuntu desktop lol. Ubuntu server is not any different then desktop. The only difference is the applications you can choose to install right from the start.

If you are looking for something a little speedier, try Xubuntu. Gnome is a memory hog. I honestly think you would be 10 times happier with Zentyal. It does everything you are looking for and will run much better on your hardware. Plus, once again, its free and is better documented. Run a session in virtualbox and you will see what I am talking about.

---

### Post by azzid on 2011-04-25
> **collisionystm said:**
> if you are using server why are you running a GUI??

It seems my communication skill is a bit lacking. ;)

I am not running gnome on the firewall, that is a clean ubuntu server.
I do, however, run gnome on my desktop machine.

It is on the desktop machine I would like to easily access the load etc. on the firewall.

---

### Post by collisionystm on 2011-04-25
Hmm.... 

Install ntop

```

http://www.ntop.org/overview.html

```

---

