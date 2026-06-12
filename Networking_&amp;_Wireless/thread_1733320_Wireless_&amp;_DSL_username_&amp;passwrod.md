---
title: "Wireless &amp; DSL username &amp;passwrod"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by mohamed shawkey on 2011-04-19
Hello All ,
i hope some one will help me in this .  ok i have a dsl conection with user name and password i can log in with my wired network but in wireless i can't configure it , there is no user name or password in windows seven i just login to my wireless connection then use the user name thats it . i tried wicd but the same thing . oh i am using ubuntu 10.4

thanks for all .

---

### Post by dineshs on 2011-04-20
> ok i have a dsl conection with user name and password i can log in with my wired network but in wireless i can't configure it How did you configure the connection for wired?Using DSL tab in network manager or pppoeconf method?
Does [this]("http://ubuntuforums.org/showpost.php?p=9857165&postcount=10") help?

---

### Post by mohamed shawkey on 2011-04-20
Than you Dear [dineshs]("http://ubuntuforums.org/member.php?u=253252") , 
I am sorry but it did not help me ... at all .
Maybe it's my fault ok .. here is my problem again ... in my country our isp give us user name and passwords :D strang right :P ( sorry i am kidding:lolflag: ) and i bought a wireless modem and it works so good. Now in ubuntu I did not say that i have any problem with my connection i can install it so well and i can log in to my wireless network . i am asking for how to put the user name and password like what i am doing in windows cause i can't have any connection with out them. how to make from the network interface and from the terminal too . 

And really Thank you you topic is so good .:KS

---

### Post by dineshs on 2011-04-20
How do you connect in windows? Do you use a PPPoE dialler with username and password?

---

### Post by mohamed shawkey on 2011-04-20
I  have windows 7 . yes i have a pppoe . i am rying to say that i do not have any hardware problem . please try to help me .

---

### Post by mohamed shawkey on 2011-04-20
My laptop is HP , i did upgrade to ubuntu 10.10 now . the same thing ](*,) . i am asking after connecting to my wireless where to put my user name and password that's it .:oops:

---

### Post by dineshs on 2011-04-21
You need to try the link given in post #2.When you do ```
sudo pppoeconf wlan0
``` it will ask for username and password.

---

### Post by mohamed shawkey on 2011-04-21
You are right maybe i was too lazy to move my hand .... thank you i did it .:guitar:

---

### Post by dineshs on 2011-04-25
Please mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") via thread tools

---

