---
title: "What software do I need to login to a remote Linux box on my network?"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Roobert on 2006-06-02
I'm not sure how to go about logging in remotely to a Linux box that I can see on my network. I've never done this before, so please be verbose. I have set up a shortcut on my desktop that lets Nautilus browse the contents of the remote machine, but I want to be able to launch programs and such. 

I'm using Dapper, the remote machine is Red Hat 9, I think.

---

### Post by s31523 on 2006-06-02
In the Internet menu there is a Terminal Server program that you can use.  On the host machine install VNC and set up a VNC server then use the Terminal Server Client to connect to it.  If you need more info, let me know.  I'll give specifics later when I am at my machine.

---

### Post by az on 2006-06-02
'love Halifax!

You can ssh into your other box.  The ssh client is already installd so you can ssh out of that box, but you need to install the ssd server (deamon) on that box so that you can ssh into it.

Just install the ssh package.

Then from your other computer do

ssh -X me@192.168.0.2

And you will get to a login on that box.  Anything you launch will run on that box, but the graphical display will happen on your screen.

---

### Post by Roobert on 2006-06-02
[QUOTE=azz]'love Halifax!

You can ssh into your other box.  The ssh client is already installd so you can ssh out of that box, but you need to install the ssd server (deamon) on that box so that you can ssh into it.

Just install the ssh package.[/QUOTE]

<snip>

Thanks! I just moved back from a long stint in the country...I'm loving the city life again!

I'll check with my sysadmin if ssh is installed on the remote machine. I don't have permissions to install software on it, unfortunately.

[QUOTE=s31523]In the Internet menu there is a Terminal Server program that you can use.  On the host machine install VNC and set up a VNC server then use the Terminal Server Client to connect to it.  If you need more info, let me know.  I'll give specifics later when I am at my machine.[/QUOTE]

Thanks, I may try this route depending on whether the ssh method pans out or not. I tried launching the Terminal Server program, but couldn't connect, mostly because I'm not sure of the proper domain of the remote machine.

---

