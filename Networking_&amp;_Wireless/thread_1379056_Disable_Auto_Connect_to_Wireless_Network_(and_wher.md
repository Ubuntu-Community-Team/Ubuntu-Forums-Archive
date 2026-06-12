---
title: "Disable Auto Connect to Wireless Network (and where is Network Manager?)"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by mac1984user on 2010-01-12
Hello,
 
I've just installed Ubuntu on my girlfriend's computer and have everything up and running quite well, (save for the built-in webcam). Wireless works flawlessly. However, my girlfriend plugs directly into the network (unless she's in the library) and is not interested in auto connecting to wireless networks that other students are running from their rooms. Is there a way to prevent Ubuntu 9.10 from auto connecting to just any available wireless network? At the moment, a screen pops up on start-up asking to enter a WPA password for the wireless network next door. It's just mildly annoying having to click 'Cancel' every time the computer starts up.
 
If there's a solution (preferably not in Network Manager), I'd be grateful. For some reason, though Synaptic Package Manager states that I have Network Manager installed, it does not appear in any of the drop down menus. If there's a way to use Network Manager, I'm happy to go about it that way after I can figure out how to access it.
 
Thanks for your help.

---

### Post by djchandler on 2010-01-12
If you right click on the Network Manager Applet, you will get a box that shows a couple of checkboxes by **Enable Networking** and **Enable Wireless**. Uncheck **Enable Wireless**.

The network manager applet varies by icon theme, but in the current release, the default looks like the attachments.

---

### Post by AggravatedGestalt on 2011-01-26
I fear am going to get a reputation for pugnacity. This is not my intention. My intention is, like the first person to post here, to disable NetworkManager from auto connecting to wireless APs without using NetworkManager; for example, gediting a config file or something. I do not want to disable wireless, or even have to look/click at NetworkManager to accomplish this. As yet another esoteric nanny application written by control freaks, I need an actual answer from someone, and not a patronizing reply. If this is not possible, no surprise, and OK; but tell me so. 

I would prefer to use wicd (no auto by default!), but Ubuntu seems unfriendly to this fine program, and I cannot get it to properly function since Lucid LTS.

---

### Post by kg4cjv on 2012-11-24
> **AggravatedGestalt said:**
> I fear am going to get a reputation for pugnacity. This is not my intention. My intention is, like the first person to post here, to disable NetworkManager from auto connecting to wireless APs without using NetworkManager; for example, gediting a config file or something. I do not want to disable wireless, or even have to look/click at NetworkManager to accomplish this. As yet another esoteric nanny application written by control freaks, I need an actual answer from someone, and not a patronizing reply. If this is not possible, no surprise, and OK; but tell me so. 

I would prefer to use wicd (no auto by default!), but Ubuntu seems unfriendly to this fine program, and I cannot get it to properly function since Lucid LTS.


Agreed, I have my system setup as an Access Point and network manager keeps popping up wanting to connect to a neighbors wifi. Everytime this happens hostapd freaks out and I have to restart it. Please help if anyone has any suggestions.

---

### Post by wildmanne39 on 2012-11-24
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

