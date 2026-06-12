---
title: "A problem driving me crazy with network manager :("
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by makaki on 2010-04-10
Hi guys, I live in the campus dorm in my university and we use DSL for internet. I created a new DSL connection in the network manager and entered the info of my account. But the problem is that I don't get connected! 

It sometimes get connected and sometimes not. 
I have to reboot Ubuntu like 6 times to get it connected. I tried my info with Windows and everything works perfect. I tried in Windows to disconnect and reconnect many times and it works fine. In Ubuntu I have to reboot a lot of times to get it connected! This thing is driving me crazzzzy :(

I hope you can help.

p.s. I tried to change the authentication protocols but nothing seems to work :(

AFAIK the sever is running on a Linux distro.

[COLOR=Red]EDIT: Log file when it couldn't connect.[/COLOR] [http://pastebin.com/rnHTJGDm](http://pastebin.com/rnHTJGDm)

[COLOR=Red]EDIT 2: Log file when it get connected:[/COLOR] [http://pastebin.com/VAwBKttP](http://pastebin.com/VAwBKttP)

---

### Post by makaki on 2010-04-10
In Windows I have to provide these info:
username, password and service. I provided those info in Ubuntu also.

Should I provide MAC or other info in Ubuntu? In Windows I don't have to provide other info.

---

### Post by stilling on 2010-04-10
have you tried to use " sudo pppoeconf " in terminal follow the steps enter user password with other words not to use network manager


hope this helps you

---

### Post by makaki on 2010-04-10
I tried it, but I can't find a way to enter the "service" info. Also when I tried it, I found a connection in the network manager in the Wired section, and I wasn't able to remove it! Also I wasn't able to connect again to DSL. I had to format Ubuntu :(

I couldn't find a way to remove what pppoeconf did in the community documentation.

---

### Post by makaki on 2010-04-10
Please check that I edited the first post and added the log file when it get connected.

---

### Post by stilling on 2010-04-11
i saw that but if you whant to have a dsl connection just try to understand 
your isp ( internet service provider ) gived you a username and a password that connects you to the internet but first you must make the physical connection that means the cable into your network board then open terminal run " sudo pppoeconf " pppoeconf will automatically see what network board has an DSL connection in username box type your username in password box type your password hit yes to almost everything but pay attention and read all well you don`t need to enter a name for your isp so i hope you understand this and helps you a little bit
sudo pon dsl-provider ( starts the connection if falls )
sudo poff dsl-provider ( stops the connection )
plog ( shows you info about connection )

more info you can find [---- > HERE]("http://manpages.ubuntu.com/manpages/hardy/man1/pon.1.html")


I hope that this will help you

---

### Post by makaki on 2010-04-11
@[stilling]("http://ubuntuforums.org/member.php?u=815886") I need to type the "service". It won't work without adding it. I read the whole community documentation page about creating a dsl connection. I couldn't find where to add that also couldn't find how to remove the connection I made.

---

### Post by stilling on 2010-04-11
ibelieve that you have karmic koala ubuntu and you can`t connect dsl from network manager where you can add service and all you need
for that follow this link if you have a backup internet line [---- > HERE]("http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10")
and do it from network manager like is shown in there


hope this really helps you

---

### Post by makaki on 2010-04-25
To solve my problem I'm thinking of buying this:
[http://www.sitecom.com/Wireless-Router-54g/WL-607/p/699](http://www.sitecom.com/Wireless-Router-54g/WL-607/p/699)

But the question is: Is it possible to create the connection from inside this device? i.e I want to purchase it so I can make the connection from inside the device and then connect to the Internet through wireless via this device. Is this device only a wireless access point or can it make a broadband connection like what I want?

Please help.

---

