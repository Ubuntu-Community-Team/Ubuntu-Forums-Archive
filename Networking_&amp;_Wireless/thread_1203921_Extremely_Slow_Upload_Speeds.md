---
title: "Extremely Slow Upload Speeds"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by jtdeloach10 on 2009-07-04
I am running a 9.04 server that is basically a file server, I have it hooked up with my normal VPS server so it can just be like a files.xxxxxxx.com with a route to my ip. <- thats unimportant :D

I have broadband internet from Cox, this server is a little old it has a 900 Mhz processor with 128MB memory. Anyways it has a top of the line Netgear Wireless Card. Download speeds like from the repositories aren't bad, about 150kb/s, upload speeds are miserably slow at about 80 kb/s! There is a problem I KNOW, because wether I download it from local (192.168.1.x) or IP (70.xx.xxx.xx) or Domain-Name(files.xxxxxx.com) its all the same speed, 80kb/s. My other computers get about 400kb/s down and 300kb/s upload. 

I would like some help diagnosing the problem and hopefully fixing it.

Note: All computers in my house are wireless (yes, even the server)
Note2: I plugged it in once (had a gigabit card, but my router is 100mb) and it got the exact same 80kb/s.
Note3: It's not that hard drive I have tried it off 3 different harddrives, even a USB and its all the same speed.
Note4: I could care less about the servers down speed the upload is what I want for a file server (It runs Apache).
Lets find this problem, and increase its speed to around 200-300kb/s upstream!

---

### Post by Maliron on 2009-07-08
I kind of have the same problem with my laptop. 

Though not to the degree you are. 

I am running Jaunty and I work for an ISP. 

I am currently connected wired at 100Mb/s. If I run a speed test ([http://speakeasy.net/speedtest](http://speakeasy.net/speedtest)) I get about 60Mb/s, which is fine, that is along the lines I would expect given that I am sure the server can't throw me my full line rate, and even it if it could there would overhead. My upload speed though is clocking in at just over 7Mb/s. Now I know there are people saying "What a putz, he's complaining about 7M upstream!" but personally I think this drastically different speed is unacceptable. 

I really hope someone has some clue as to what can be causing our issues, I get the feeling they are somehow related.

Have you tried to disable ipv6 yet? That seemed to make a fair amount of difference on my system.

---

### Post by daemonkorn on 2009-08-25
hello... try going to this site it may answer your question and resolve your problem with slow connection.... this is for wired/wireless/wimax connection **[http://daemonkorn.blogspot.com/](http://daemonkorn.blogspot.com/)**

---

