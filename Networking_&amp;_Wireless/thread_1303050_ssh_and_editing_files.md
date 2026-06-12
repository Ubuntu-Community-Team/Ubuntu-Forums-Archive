---
title: "ssh and editing files"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by gypsumwolf on 2009-10-27
If I have an html file on my server and I want to work on that file with Bluefish (on my laptop) can I somehow do that though ssh instead of having to scp the file back and fourth?

---

### Post by shaggy999 on 2009-10-27
if your server has bluefish installed on it, you can run the application remotely I think if you use the -X option.

So: ssh -p port -X user@host

Then when you get to a console just execute the application, I'm assuming it's 'bluefish' so just type that and hit enter and it will begin running on the server but the application window will appear on your laptop.

EDIT: Actually, I guess there's some config stuff you have to do. here's a link:
[http://www.cyberciti.biz/tips/running-x-window-graphical-application-over-ssh-session.html](http://www.cyberciti.biz/tips/running-x-window-graphical-application-over-ssh-session.html)

---

### Post by Lars Noodén on 2009-10-28
That can be simplified even a step further, again assuming bluefish:

[INDENT][FONT="Courier New"]ssh -X -l gypsumwolf *xx.yy.zz.aa* bluefish[/FONT][/INDENT]

If the session times out, which it shouldn't if you are active, you can have the client send a heartbeat at intervals

[INDENT][FONT="Courier New"]ssh -o 'ServerAliveInterval=60' -X -l gypsumwolf *xx.yy.zz.aa* bluefish[/FONT][/INDENT]

---

### Post by gypsumwolf on 2009-10-30
Thanks! I will try that after I finish updating my server. And I will post results here.

---

