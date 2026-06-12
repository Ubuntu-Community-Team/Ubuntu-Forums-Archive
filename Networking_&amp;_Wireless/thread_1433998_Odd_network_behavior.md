---
title: "Odd network behavior"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by minimustangs on 2010-03-19
I've been compiling this throughout the day, sort a log of notes...

OK, so yesterday I was investigating how to improve my connecting (DL) speed with Azureus (Vuse). I looked at port forwarding issues, network issues (NAT) - according to the icons in the program I didn't have any trouble, except for slow transfers. I am aware of the dynamic nature of torrent transfers so maybe all of this has nothing to do with anything except the swarm I am a part of. 

After a couple days of UL and DL a specific large file, and having a reasonable number of seeds and piers, I was still trying to improve my <10kb/sec download speed. My maximum connection speed through my ISP is 320K/sec (somehow that related to 2.6M/sec.). 

I installed firestarter and other than assign a port I needed, I didn't notice any appreciable improvement or change.

Today - early this morning i was messing with things again and at one point tried to connect via ETH0 instead of wireless (as I have been and am currently connected). My connect speeds dropped to ZERO, and I lost my membership in the swarm. I took the opportunity to reboot hoping that would clean things up. Oh yeah at some point just before rebooting I ran as root : iptables -F. This didn't do anything either. SO I rebooted. 

After a few minutes getting back into the swarm and attempting to get my tracker re established ( for some reason it was now "broken") my connect speeds when through the roof. I have been constisitently abouve 200kb/sec...well above swam average of 80 kb/sec and in most cases I am in the 290 to 300 kb/sec area. This is of course making a great difference to my down load - which will finish in a matter of hours not days...at this rate. 

Problem is... I can't connect to ANYTHING else. Mail not working, WWW not connecting. It's not traffic relate as I tried connecting to those before launching my torrent client.

I don't know what exactly happened...it's a godsend and a curse at the same time.

Any guesses? I'm not sure if it has something to do with iptables -f or firestarter. Whatever it is, I'd like to be able to replicate as necessary these setting when I'm wanting to DL torrents and revert to more "normal" settings for general internet use.

I don't know what I broke to fix it.


Update...at about 4:20PM my glorious DL rate came to a crashing halt - I guess it had to do mmore with the Seeeders in the swarm than it did my efforts to improve things. 

I'm now hovering at about 50kb/sec which is certainly beter thatn the <10 I was achieving this week, but a far cry from the near 300's...

I've managed to restore my WWW and mail connect issues, don't know ehre they went in the first place. I would think that my tracker issue is resolved since it required HTTP.

Now my situation is reversed...Swam Avg is ovwe 200kb/sec and I'm less than 50. But WWW. and mail are working.

I'm thinking that if I somehow disabled www and mail before this might have freed up bandwidth and that's how I was able to get those great Dl speeds?

---

