---
title: "OpenVPN/Adito setup: Extranet access"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by tylersontag on 2010-02-25
Alright, I’ve been trying to get this fixed on my own, but I think I’m missing a fundamental principle and no amount of scripts or hacks is gonna take place of that.  I have adito/OpenVPN installed on my media center.   It runs fine and I can access adito in my internal network from other computers just fine.

But, the whole point is I want to be able to access it remotely!  Now, I had previously made a run at an external FTP site and failed miserably at that, and I think its all coming down to me not knowing how to configure my own router.

I have a Netgear router, I can log into it and under Router status I can get what looks to be my routers external IP address.   But if I try to access it at [https://XXX.XXX.XXX.XXX:4433](https://XXX.XXX.XXX.XXX:4433) (didn’t want to use the default port, 443)  I get nothing.  

So, my main problems as I understand them are:
1)	I need to clear the firewall on my router to allow traffic in/out of my reserved port 
2)	I need to forward incoming requests on that port to the static internal IP of my media center
3)	I really would like a more reliable way to verify the info im getting from my routers admin settings page is actually my external IP, is there a command for this or a website that will tell me?


And, as I said earlier, I think I’m missing something fundamental, this is the list I thought up, if im missing any steps, I would love to know what they are.  Thanks!

---

### Post by cruelsun on 2010-03-16
Try the following: 


[LIST]
[*]Port forwarding is essential, I would think.
[*]Try to connect without "https" from outside. That protocol may not be recognized coming it.
[/LIST]
Post the model number of your router, someone here may be able to help you better, know the features and restrictions of your router.

---

### Post by tylersontag on 2010-04-12
Solution:  Crummy Netgear router.

I'd setup port forwarding several times (for this and an FTP site) and never goten it working.  I just moved out and couldn't take the netgear with me and found an old linksys router.  Did the same port forwarding steps on it and it worked the first time out of the box.

It would be helpful, if anyone knew of some PING or some other commands that could test if an external port is hitting the internal box you are wanting it to hit...

---

