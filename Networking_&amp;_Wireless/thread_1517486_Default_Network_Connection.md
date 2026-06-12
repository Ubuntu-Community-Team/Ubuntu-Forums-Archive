---
title: "Default Network Connection"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by a.kazemi on 2010-06-25
Hi my friends
I have Ubuntu Netbook remix 10.04 on my Asus n10jb and an Ubuntu 9 on my desktop and I have a wireless router with internet connection.
I want to connect my desktop to my netbook with ethernet connection and share the wireless internet connection between both PC and Netbook. I done it just one time and it works well. just connect to the wireless connection with netbook and make a wired network with static ip 192.168.1.1 and my router default gateway and let the PC get IP automatically they work very well but after that each time I try to do it again my netbook put the ethernet connection default one and lose internet connection! and when I disconnect ethernet it ping the google ip ( 8.8.8.8 ) and find internet connection again.
please help me how to define wireless connection the default one?
thanks all experts:confused:

---

### Post by pastalavista on 2010-06-25
never mind... I don't know

---

### Post by Iowan on 2010-06-25
Probably more elegant ways exist, but...
You could try un-checking the "Connect automatically" option for eth0. It'd still be there when/if you need it, but *shouldn't*:-k wind up as default.

---

### Post by a.kazemi on 2010-06-25
I have checked all the possible options uncheck the automatic connect check it again and same for all users but all failed.
I know the main problem is the default network . in a way I have to change default network connection.

---

### Post by a.kazemi on 2010-06-25
At last I find the way:guitar:. I share it here of others face with this problem solve it::lolflag:
for sharing your wireless or other connection through ethernet connection follow these steps:
first delete all other connections except the original connection that have internet.
second make a shared to other computer connection in the pc that want to route connection or connected automatically to internet.
third make a connection with automatic DHCP in the destination pc which want to connect to internet through the other one.
then let them to share and get their IPs.
if at this time you test the ping 8.8.8.8 in terminal it shows you that you have internet connection or not.
hope works for you.
more questions:
[email]alireza.kazemi@live.com[/email]:popcorn:

---

### Post by Iowan on 2010-06-25
Glad you had some luck... pleased that it was **good**.  ):P
If the problem stays fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

