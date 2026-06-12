---
title: "Controlling ubuntu from Android (Java issue?)"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by bone2006 on 2010-05-23
I've seen a few apps that allow you to play music, movies..etc from android, but I'm looking for a VNC type application.  I tried a few VNC programs in android and couldn't get it to refresh back to the phone.

I ran remotedroid on windows and was really impressed. I am having trouble running in on ubuntu.

[http://www.remotedroid.net/](http://www.remotedroid.net/)

It says just run the jar, if i double click on it a compression utility opens up, if I right click and select open with OpenJDK java 6 runtime, then a I get the message:

The file '/home/user/Downloads/RemoteDroidServer/RemoteDroidServer.jar' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Any help or suggestion

UPDATE
I just did chmod 700 and it's running, but can't get it to work 127.0.0.1 is what it's showing as the IP and I'm not able to get on, any help is appreciated

---

### Post by cariboo on 2010-05-23
This isn't a Cafe question, moved.

---

### Post by Xanko on 2010-08-26
127.0.0.1 is the IP for localhost (to connect your machine to itself) You need to right click on your network manager icon and goto connection information to retrieve your network IP and connect to that IP.

ifconfig in a terminal window will also show your network settings and the ip address of your system.

---

