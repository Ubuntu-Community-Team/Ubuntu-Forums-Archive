---
title: "Bridging Connections"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by shro0ms on 2010-06-28
Is there a way to bridge my wireless connection with my LAN connection. I know on windows i can highlight both and then right click and select "bridge connections." is there a way to do this on ubuntu?


Thanks

---

### Post by Iowan on 2010-06-28
Like for [Connection Sharing]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless")? 
[Here]("https://help.ubuntu.com/community/NetworkConnectionBridge") is an article on Bridging, but it's getting a little old...

---

### Post by shro0ms on 2010-06-29
thanks Iowan, i'll try those. 

If i wasn't specific enough in my post, its to connect my xbox to xbox live via my wireless connection on my desktop. so the ethernet cable is connected to the xbox and my computer and the bridge allows the xbox to receive internet connection.

---

### Post by Finalfantasykid on 2010-06-29
Funny I was attempting to do the exact same with my PS3 like yesterday.  Unfortunately I failed miserably.

Those links you provided appear to be 

Internet <--Ethernet-->Ubuntu PC<--Wireless-->Device

but what I think we both want is

Internet <--Wireless-->Ubuntu PC<--Ethernet-->Device

I've been having many wireless issues with my PS3(I don't think it likes my router very much), which is why I want to try connecting it via my laptop, which never drops it's connection.

---

### Post by arsenic23 on 2010-06-29
I think you can just install firestarter and do this all much easier, but it has been a long time since I messed with it so I may not be remembering everything perfectly.

---

### Post by shro0ms on 2010-06-29
Finalfantasykid, that's exactly right. the wireless on my desktop connects me to the internet (on my desktop) and the ethernet cable connects the xbox to my pc, and the bridge will then bridge (redundant lol) the wireless and the ethernet. 

Im not trying to connect the wireless on my pc to the device, however

---

### Post by mosquetero on 2010-06-29
I am not sure how much you can configure a XBOX connection but at my home I have:  Internet<--Wireless-->PC-Ubuntu<--Ethernet-->PC-Windows, and the PC-Ubuntu provides internet to the Windows one. I am using a proxy in my PC-Ubuntu to do that. If you think that could be a solution, I'll be glad to go further in my explanation :KS

---

### Post by arsenic23 on 2010-06-29
This is the easiest way I know to share internet through a linux machine:

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

It only takes about 30 seconds once you get firestarter up.

---

### Post by shro0ms on 2010-06-29
I found a solution to the problem. It doesn't require configuring anything or using firestarter or anything like that.

Here's the thread: [http://ubuntuforums.org/showthread.php?t=1180463](http://ubuntuforums.org/showthread.php?t=1180463)

Sorry if i wasted anybody's time with this thread.

Hopefully this will solve your problem as well, Finalfantasykid.

---

### Post by Iowan on 2010-06-29
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

### Post by Finalfantasykid on 2010-06-29
Is a cross over cable necessary?  If so, how do I know if the one I have is one.  I am using the cable which came with the PS3.

---

### Post by shro0ms on 2010-06-30
i imagine any ethernet cable would work. Personally, I am using a cat-6 cable

---

### Post by Finalfantasykid on 2010-06-30
Well that is what mine is labeled as.  I guess I will keep trying.

I got as far as my PS3 knowing that my laptop is there.  It got an IP address, but could not connect to the internet.

---

### Post by shro0ms on 2010-06-30
did you edit eth0's IPv4 settings and change the method to "shared to other computers"?

if its not working after that, perhaps you need to change some settings on the ps3. not sure about the ps3 and what you need to do on it, but i'll check in the morning what settings i have on my xbox.

---

### Post by shro0ms on 2010-06-30
My IP settings and DNS settings on the xbox are both set to "Automatic".  Again, i don't have a PS3 so i don't know what kind of settings you  have. try googling this same topic except for windows and see if you can  find information that way.

---

### Post by Finalfantasykid on 2010-07-01
Awesome it worked. and I didn't have to use firestarter :)

---

### Post by shro0ms on 2010-07-01
glad i could help :)

---

