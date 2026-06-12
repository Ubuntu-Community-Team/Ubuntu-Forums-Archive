---
title: "Cannot get X11 forwarding to work on Ubuntu 11.04!"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by GarlicGoldfish on 2011-10-26
Hello,

I have two Ubuntu 11.04 machines connected to a network and when I try:

[B]ssh -X [email]user@xxx.xxx[/email].x.x   
[/B]
and open a program I am getting an error message that says 

[B]x360@SS:~$ firefox
Error: no display specified
x360@SS:~$ xterm
xterm Xt error: Can't open display:
xterm:  DISPLAY is not set
[/B]
This is odd as I have another machine that works fine, and I believe I have installed all the necessary packages.

It seems that the DISPLAY variable isn't being set properly, but even when I manually set the DISPLAY it is not working

I don't know where to start, and any help would be appreciated.
Thanks!

---

### Post by GarlicGoldfish on 2011-10-26
Update: strange.  so i can get X11 forwarding to work fine when I remotely login on my machine running windows using putty and xing.

However, X11 forwarding does not work when I SSH from the same machine in Ubuntu....

---

### Post by GarlicGoldfish on 2011-10-26
finally solved, that was the dumbest problem ever that was causing it!!!!
would never have imagined that was the problem until i stumbled upon some thread on the net.

Thanks all.

---

### Post by winstonschmidt on 2012-03-15
Wow, that last post was ...not very useful :-/ 
It's great that you solved you problem - care to share how?


PS. for anyone searching I found this IPV6 related bug:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422327]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422327")

---

