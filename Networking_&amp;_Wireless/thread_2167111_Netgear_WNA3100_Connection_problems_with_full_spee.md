---
title: "Netgear WNA3100 Connection problems with full speed download"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by paul19 on 2013-08-12
Hey there. I have a WNA3100 and I got it working with ndiswrapper and the driver [COLOR=#333333][FONT=Lucida Grande]bcmwlhigh5.inf[/FONT][/COLOR]. I have to say i am using linux mint but i think it should be the same.

Then I got a new router (Technicolor TC7200) which replaced the very old one from my provider and now i have troubles with the connection (with Windows 8 dualboot I have no issues - works like a charm):

When I download with full speed or try to open multiple websites at the same time then the connection is interrupted after 1 minute. I can not surf anymore, no more website is available and all downloads are down to 0 kBit/s. But the manager shows it is connected.
I have tried to [COLOR=#333333][FONT=Lucida Grande]limit the up and downstream with:[/FONT][/COLOR]

```
sudo apt-get install trickle
sudo -s trickle -u 5000 -d 5000 apt-get update
```

but still the same issue. I must say that i only installed ndiswrapper and then immediately the driver. No more editing apart from editing the up- and downstream with tickle.

Anyone knows a solution?

---

### Post by Bucky Ball on 2013-08-12
***Post moved to own thread.***

Welcome and a head's up. Your problem is NOT the same as the original poster's on the other thread. What you've done and what you're doing are different and no doubt the rest of you hardware apart from the wireless card are different, too.

Hijacking threads is a bad idea for a lot of reasons; dilutes community effort, is unfair to the original poster, confuses the issue as brings a whole new set of problems to the table and, worst of all, burying yourself 30+ posts deep on someone else's thread with a title that is unrelated to your problem won't get you much help (but will probably get the suggestion to start a new thread). Anyhow, being on your own thread greatly improves your chances. Keep an eye on the other and give or take what's appropriate. 

There's plenty of room on the forums. Good luck with a fix for this. ;)

PS: If you'd like to change the thread title, feel free for the next half hour by 'Go Advanced'. If you miss that window, throw me some suggestions if you want to change it.

BB

---

### Post by paul19 on 2013-08-12
Thanks for creating a new thread Bucky Ball!

Now i think the problem is 802.11N. My old router did not have N, the new router does have N and maybe this is the reason for the problem.

But this damn router doesnt have the option to turn N mode off, only 2 options (1. only N mode / 2. BGN mode). So i have to deactivate this on my adapter but i have no clue how to do this in Linux mint 15.

Anyone can help me to deactivate N mode?? Or maybe edit the original windows driver and deactivate N then reinstall in ndiswrapper with the edited driver? I dont knwo if this works.##thx in advance.

---

### Post by Bucky Ball on 2013-08-12
Have you tried BGN setting on the router?

---

### Post by paul19 on 2013-08-13
Yes tried both. But I think only N mode is prefered becasue I can see the Information about the Wireless connection and its always above 54MBit/s so it can not be B or G because G is up to 54Mbit/s.

It happens only at full speed when i'm downloading torrents with the maximum of my bandwith or if i run the updates of lnux mint, but not when i'm only surfing.

---

