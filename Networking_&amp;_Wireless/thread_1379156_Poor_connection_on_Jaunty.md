---
title: "Poor connection on Jaunty"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by Radissthor on 2010-01-12
Hello Everyone,

I have this problem that, according to what I've read on the web, is a well-known bug. The thing is that the "solutions" were either nor helpful or I could not really understand them very well (total Noob)

I'm trying to connect to the wireless netwrok of my university, which does NOT require any password. When the computer starts is automatically connects to the network and it always worked well, but now a message appears that says "authentication required" and it says that the network requires some sort of password or key. This is weird because it had never given me the problem. The options in the box are "Cancel" and "Connect", but "Connect" cannot be marked. There's also a dropdown box in the box that says "Security Type" and the option is "none". No other option is available for marking. 

After canceling the message and trying to connect like 50 times, I finally got a very poor connections. My email took forever to open and I opened the terminal to download something that someone said had solved the problem

```

sudo apt-get install linux backports-modules-jaunty
```

But it has taken forever to download, which proves the connection is working but it's in really bad shape. 

Any hints on how I may solve this? I read several bug reports and fixes similar to the problem, but they were very old (apparently a bug that was in Gutsy and then continued in some cases in Jaunty).

I appreciate any help you may provide. Thanks in advance...:)

EDIT: Now I definitely can't connect. One strange thing was that at my house I couldn't connect either, but this time because I didn't even had the wireless option available anymore. I went to Hardware Drivers and realized 2 things:
There were 2 drivers recognized, which is weird because I had always had only one, which is the Broadcom STA Wireless Driver, and there was another one, also wireless related,. but which name I don't remember
Both drivers were deactivated, which again is strange because the STA was always activated before. 

I activated the STA driver only. because I feared that two activated wireless drivers may have conflicted with each other. The Wireless started working again and I connected to internet with no problem. My home connection, by the way, needs a password.

Now, back in University, whose wireless does not need password, the same problem happens. It says "Authentication required by wireless network" "Passwords or encryption keys are required to access the wireless network 'UC'." The a dropdown box with the title "Wireless Security" and with the only option available marked: "None". The the options in the dialogue boz are Cancel and Connect, which cannot be chosen. 

I went to Hardware drivers again, and now only the STA driver is shown, and it IS activated... I'm really at a loss here...

PLEASE HELP!!

---

### Post by Radissthor on 2010-01-13
It turned out it was a problem with the wireless of the whole University... so no help required anymore...

I'd say thanks for the help, but this has been the first time a request for help has gone unanswered for so long... well, it's how volunteer work works I guess....

---

