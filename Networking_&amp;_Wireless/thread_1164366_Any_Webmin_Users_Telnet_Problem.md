---
title: "Any Webmin Users? Telnet Problem"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by roystreet on 2009-05-19
Hello,
    I'm using ubuntu server & I have successfully used webmin for a lot of things.  It is an excellent program for administering my server.  Now there is a telnet area of webmin & I thought it would act as a terminal so I can directly type in commands, etc on my server without going physically to my server.  Do I understand this wrong?  As a linux server, it sits by itself without a monitor or keyboard hooked up to it & it's just as happy as it can be.  Occasionally I actually need/want to log into the server & type some commands, etc.  I thought the Telnet area would act similar to a remote desktop, except of course my server has no desktop.

When I go to the telnet area of webmin it asks for my log on & password, I think input it. Then the little black box where I would assume the terminal would show up stays black.  It states on the bottom right side offline. While it's asking for the username/password it states online.  It would let me type anything in that box at all.

Any thoughts?  Am I thinking the telnet area is for something it isn't made for?

Thanks,
  ~roystreet

---

### Post by roystreet on 2009-05-20
OK folks...I consider this solved in a way, but not totally.:-k

Instead of continuing to mess around with webmin to log into the system, I downloaded PuTTY.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")

It worked the first time.  I downloaded an exe file & so no install was needed.  It uses ssh.  In less than a minute basically I could get on my server via my win machine & start running commands. 
[COLOR="Blue"]**Perfecto!!**[/COLOR] This was exactly what I was looking for!

Now the part that wasn't resolved is why webmin doesn't work in that area?  Any thoughts? 

If anyone is having this problem, here is a working solution

~roystreet

---

