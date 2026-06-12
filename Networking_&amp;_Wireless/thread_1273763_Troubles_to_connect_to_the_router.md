---
title: "Troubles to connect to the router"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by DanyFlorence on 2009-09-23
[SIZE=4]**[SOLVED]**[/SIZE]
Hello there, I'm new here. I need your help about a problem I encountered today. I installed Ubuntu 9.04 on a Pentium Duo PC in Double-boot mode with Windows XP Pro. 
The problem is that, when I try to connect directly to the router, Mozilla doesn't answer. I explain myself better, I can surf on the net, I can download and internet works fine but I can't access to the router; when I insert [http://192.168.0.1](http://192.168.0.1) on Mozilla, it asks me the password and username but I can't see the main page. I need it because I must connect/disconnect to internet and, at the moment, I have to reboot the pc starting Windows XP (router, infact, works perfectly with Windows) in order to connect or disconnect from the internet.
But I've got another pc with Ubuntu 9.04 and I can properly connect and enter into the router. I can't find the problem.

I hope I could explain myself good in English. Thanks in advance,
Daniele.
[SIZE=4]**[SOLVED]**[/SIZE]

---

### Post by DanyFlorence on 2009-09-24
Can nobody help me? Please :)

---

### Post by DOSn3rd on 2009-09-24
Do you use Firefox or Internet explorer to connect to the router in Windows?

---

### Post by wojox on 2009-09-24
Have you downloaded:

```
ubuntu-restricted-extras
```

It may be a java problem. My router index is java based.

---

### Post by DanyFlorence on 2009-09-28
I use Firefox on both, Ubuntu and Windows.

It doesn't work even with the stuff you suggested me. I guess I must re-install Ubuntu. It works on another pc with the same router.

Thank you anyway :)

---

### Post by Iowan on 2009-09-28
I'd ask whether it's wired or wireless - but I may be a couple of minutes late...

---

### Post by DanyFlorence on 2009-10-07
Hello there, I solved it! :)
There was a problem about [MTU](http://en.wikipedia.org/wiki/Maximum_transmission_unit). Don't ask me why but when it is high it gives some problem with connections. I reduced it with this command

sudo ifconfig eth0 mtu 1492

[FONT=Times New Roman]Now it works correcty. Thanks for the help!
[/FONT]

---

