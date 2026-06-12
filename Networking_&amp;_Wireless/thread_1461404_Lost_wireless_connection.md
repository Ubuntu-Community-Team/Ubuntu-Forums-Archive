---
title: "Lost wireless connection"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Ceresetta on 2010-04-24
Computer originally working beautifully. Power up and it automatically connects to my home wireless network. Then I did the following things:
1. I made a user account for my daughter (network kept working)
2. I sought a way to have user-specific web content filtering. OpenDNS was recommended. Opened network manager and began process, which involved modifying settings on the IPv4 tab. Realizing that it was going to affect the entire computer (and not understanding what the heck I was actually doing) I backed out, setting things (as far as I could tell) back to the way they were when I started. At this point the computer no longer "saw" or could connect to the network.
 
I have two other computers (Windows) that work fine, so I don't think it's a problem with the network. Ideally I would just like to put things back to their default settings, but there is no obvious way to do this. 
 
The overriding goal here is to connect to my home wireless network.
 
Any ideas?

---

### Post by Iowan on 2010-04-24
Unfortunately, wireless is still one of my (many) weak areas. What little wireless I've done has ben to connect to unprotected WiFi hotspots. I presume you have a secured network...  I doubt it could be as simple as the Connect Automatically checkbox...

---

### Post by Ceresetta on 2010-04-25
I once called a technician in because I couldn't start my roto-tiller. He started it by doing something I hadn't thought of .... he opened the valve on the gas line. So you can't put anything past me, but I've tried with and without "connect automatically" checked but it doesn't make any difference. 
 
I assume there is some sort of diagnostic procedure I can do through the command line, but I don't know what it is.

---

### Post by NichoTL on 2010-04-25
I'm not sure what the problem is but what I would do is the following:

First we are going to remove your wireless connection profile (ie we want to start from scratch). Right-click on the network manager icon in the top-right area of your screen and select 'Edit connections...'.
Click on the wireless tab and delete the profiles (if that's ok with you).

Second check that your wireless network is (or isn't) in the list of networks seen by Network Manager. click on the icon in top-right area and tell me what you see under Wireless Networks.
If you don't see your SSID or if you see something like "device not ready", open a terminal window and type:
```
sudo restart network-manager
```
Hopefully now you should see your network in the list. Just click on it and follow the instruction. It should create a Auto-'your SSID' profile that will/should connect you every time the computer sees the network.

If there is something dodgy with any of the steps I gave you, please tell me.

---

### Post by Ceresetta on 2010-04-26
Did all that. After deleting my wireless network and left-clicking on network manager I see:
Wired network
(disconnected)
Wireless Networks
(disconnected)
VPN Connections
Connect to Hidden Wireless Network...
Create New Wireless Network...
 
No sign of my network.
 
So I opened the terminal window and typed the restart command. However, it hasn't made any difference. 
 
Since the only thing at all difficult I did after installing Ubuntu was to get Movie Player to play movies, I am beginning to think that the best thing to do is simply to reinstall the OS. I mean it used to work...

---

### Post by Iowan on 2010-04-26
From a terminal (since you know how to use one ;)): **sudo lshw -C network** should show information about your interface(s). (We're assuming the wireless switch is on.)

---

### Post by Ceresetta on 2010-04-27
I'm assuming you're all going to hate me... it's a little like the roto-tiller... the computer is new to me and, well, there's this little button ... I didn't see it ... and gosh, when you push it this nice little blue light comes on and ... well, everything works! Thank you for all your time.

---

### Post by NichoTL on 2010-04-27
> **Ceresetta said:**
> I'm assuming you're all going to hate me... it's a little like the roto-tiller... the computer is new to me and, well, there's this little button ... I didn't see it ... and gosh, when you push it this nice little blue light comes on and ... well, everything works! Thank you for all your time.

Hehe you are not the first one, and you won't be the last one either.

Please mark the thread as SOLVED...

---

### Post by Iowan on 2010-04-27
> **Iowan said:**
> (We're assuming the wireless switch is on.)That's why the hint ;)
([Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is another one...)

---

