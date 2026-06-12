---
title: "Cannot ping Ubuntu computer from laptop"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by jackwhite on 2010-02-23
Hi,

I'm a beginner at networking. 

I have an old computer I have set Ubuntu up on to use it to learn about web services, networking and sys admin.

As a first step I have installed the LAMP packages successfully. I want to reach my ubuntu computer from my laptop through my home wireless setup.

I go to Terminal and enter: 
```
ifconfig | grep inet
```

I get back
```
inet addr:127.0.0.1  Mask:255.0.0.0
      inet addr:192.***.1.104  

```

So I assume that my ip address is 192.***.1.104 right?

On the server I open a browser put this in the address bar and get to the "It works!" page so assume its correct.

I go to my laptop, put the same number in the browser and am told that there's a problem loading that page.

I figure ok, could be security or ports or something so i ping it to see if it work on that level and it doesn't.

I go to my laptop, get the ip for it and then try to ping from ubuntu to my laptop - that doesn't work either.

Pinging the router from both computers works fine though.

What do I do now? I know its probably something really basic but don't have the first clue where to look so i would appreciate any help!

---

### Post by Iowan on 2010-02-23
Check **sudo iptables -L** on each machine to see if there are rules in place (active firewall). If so, pings may be getting blocked, too.

---

### Post by jackwhite on 2010-02-24
Thanks for that. Theres nothing blocked on my Ubuntu box anyway. 

After looking around a bit i think it might be a router setting. I'm going to have to do a hard reset since my flatmate lost the admin password but I'll report back here later.

---

### Post by jackwhite on 2010-02-25
Thanks for your help lowan. It was my router settings I have the WRT300N and there is a setting called 'AP isolation'. this needs to be disabled.

---

### Post by Iowan on 2010-02-25
Wow... that's another one I'll wish I could remember. Congrats!

---

