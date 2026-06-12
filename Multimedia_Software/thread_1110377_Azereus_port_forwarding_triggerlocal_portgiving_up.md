---
title: "Azereus port forwarding trigger/local port/giving up on Linux?"
date: 2009-03-29
forum: Multimedia Software
---

### Post by tdawg on 2009-03-29
Complete noob warning: if you hate complete noobs, please stop reading and do not reply!

Ok, so I downloaded azereus and it's obviously not working out of the box (like almost every other linux software app ive toyed with) and I suspect it has something to do with my ports not being open because I ran the test and that's what it said. In my router I have trigger ports and public ports. I've toyed with the ports, not knowing if they should be the same number or not so I tested both ways, also making sure the number was in between 5000 and 6000 UDP and TCP( I know thats not the exact numbers it should be between) and still it does not work. I've updated the port in the application itself each time not knowing if I should put in the port trigger or the public port so again I tried both and still no luck. I'm using ubuntu out of the box and as far as I know I don't have any firewall software installed. My router is a D-link DI-604. 

Thanks for your help. I would really like to continue using linux but I cannot understand for the life of me why everything is so complicated and not user friendly at all. Nothing ever works. I understand that linux allows so much flexibility and control but shouldn't that be an OPTION and not a way of life? I mean, allow extreme ease of use but also allow the user to dive into the OS if he wants.

---

### Post by lovinglinux on 2009-03-29
Noobs are welcome, but that attitude of yours is not the best way to get help. This is your second thread with a title saying you will give up on Linux and the comments above doesn't help either. Post your testimonials and complains in the [Testimonials & Experiences]("http://ubuntuforums.org/forumdisplay.php?f=103") forum.

First of all, Azureus is not a simple application. The configuration of a torrent client by itself is above the skills of a lot of Windows/Linux/Mac users. It isn't supposed to work out-of-the-box on any OS, unless you buy the machine with the torrent client already installed. 

You should start using a simple torrent client. [Deluge]("http://www.getdeb.net/app/Deluge") is a great option, I use it myself. It has everything you need, a nice interface and is pretty easy to configure.

Since you are using Ubuntu out-of-the-box, then you don't have any firewall rules. Just to make sure, post the output of the command below:

```
sudo iptables -L
```

Then make sure you forward a single port from the router to your machine IP. Configure Deluge to accept connections on the exact same port. That's it.

If you don't want to much trouble, then enable UPnP on the router and on Deluge's configuration. The port will be opened automatically when you start downloading. 

BTW, it's Azureus, not Azereus.

---

### Post by tdawg on 2009-03-29
Thank you for the response. Yes I am pissed off at linux and I want you to convince me it is good, that it why I say those things. Thanks.

---

### Post by lovinglinux on 2009-03-29
> **tdawg said:**
> Thank you for the response. Yes I am pissed off at linux and I want you to convince me it is good, that it why I say those things. Thanks.

I used Windows for 15 years and now I regret not switching before. Sometimes, depending your hardware, the transition can be painful, but in the long term you will have much less problems then with Windows. Just as an example, I had  to format my hard drive and reinstall Windows every 6 months, due to performance issues. Additionally, there were painful and constant maintenance procedures, to keep it out of trouble. But I'm running Ubuntu for 7 months and sometimes I get bored, because there is nothing to fix anymore. It simply works like the first day I installed it.

---

### Post by theozzlives on 2009-03-29
> **lovinglinux said:**
> I used Windows for 15 years and now I regret not switching before. Sometimes, depending your hardware, the transition can be painful, but in the long term you will have much less problems then with Windows. Just as an example, I had  to format my hard drive and reinstall Windows every 6 months, due to performance issues. Additionally, there were painful and constant maintenance procedures, to keep it out of trouble. But I'm running Ubuntu for 7 months and sometimes I get bored, because there is nothing to fix anymore. It simply works like the first day I installed it.

I agree, I'm running the beta of Jaunty (and went through all the Alphas) just to feel like I'm doing some good. Ubuntu is too maintenance free.

---

### Post by lovinglinux on 2009-03-29
> **theozzlives said:**
> I agree, I'm running the beta of Jaunty (and went through all the Alphas) just to feel like I'm doing some good. Ubuntu is too maintenance free.

Today I started a virtual machine with Kubuntu for the same reason :)

---

