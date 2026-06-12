---
title: "Remotely connecting to mysql from XP machine"
date: 2008-09-25
forum: Mythbuntu
---

### Post by rflook on 2008-09-25
Afternoon,

I am currently teaching a group of senior school pupils about databases and want to get over to them how having a nice GUI interface to a DBMS makes your life easier. At home i am running MySQL on my mythbox and want to be able to connect to this from some form of command line interface. I thought maybe i could telnet into my mythbox and get them to connect to mysql and make themselves some tables. However im not really sure how i could do this. Any suggestions very welcome.

Many thanks

---

### Post by Eric Boring on 2008-09-25
You can SSH into the mythbox and then do whatever you like from the terminal. I just wrote up a guide for this here:
[http://blog.lib.umn.edu/welsh059/blog/2008/09/x_on_windows_you_bet_1.html#more](http://blog.lib.umn.edu/welsh059/blog/2008/09/x_on_windows_you_bet_1.html#more)

This particular guide uses Cygwin to get -X out on the XP machine, but you can also just work from the terminal and not launch any GUI apps. Or you can just use cygwin as an ssh client without setting it up for -X at all. 

Also, there are ways to use SSH over the internet. I don't use it off my home network, but others can probably tell you how to do this safely.

-josh

---

