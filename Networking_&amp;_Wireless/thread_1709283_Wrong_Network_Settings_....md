---
title: "Wrong Network Settings ?..."
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by rainbowagent7 on 2011-03-18
Hi all. I purchased a very nice wireless n router and service with a satellite ISP to improve my overall home network security and performance, but alas the connection I have now is almost as slow as when you piggyback off of someone with dial-up! Okay, maybe it's not that bad, but I'm sure it can do a heck of a lot better. Anyway, I need help at this point because I've tried everything I know how to do without screwing things up. I'm confident it is something simple (knock on wood) but I am spinning my wheels trying to research it, if someone could help I'd be eternally grateful, thanks in advance.

---

### Post by BkkBonanza on 2011-03-18
What speed is the satellite service supposed to offer? If you go to a website that offers bandwidth tests (there are many out there) then what does it say you're getting compared to what the ISP says you "should" have?

eg. [http://www.bandwidthplace.com/](http://www.bandwidthplace.com/)

---

### Post by rainbowagent7 on 2011-03-18
Thanks for the reply. The site you gave a link for showed 1.57 Mbps download speed and 51 kbps for upload speed. And to be honest with you, my girlfriend is the one who set up the account and I don't even know how fast it's supposed to be. But our machines and other hardware are all definitely capable of more than that.

---

### Post by BkkBonanza on 2011-03-18
I'm not familiar with what the norms are for satellite. I found this page below which seems to indicate that despite the high price the typical link has very slow upload speeds. You may be getting the expected speed but you'd have to contact the ISP and see what they claim you should get.

[http://www.velocityguide.com/satellite/satellite-internet-comparison.html](http://www.velocityguide.com/satellite/satellite-internet-comparison.html)

And as it mentions when latency is as high as satellite the actual bandwidth you can get is much reduced. Max bandwith is limited by the latency value on TCP networks as packets need to do a return trip for ACKs. You may do better with UDP based protocols such as torrent downloads.

---

### Post by rainbowagent7 on 2011-03-18
Stop the presses, problem solved! I knew it would be something disgustingly simple, as it turns out all of my settings and the manner I carried them out were all up to par. The culprit however came to me as I was reading a forum post @ Linksys website about a Linux user who was having the same problem and he stated that he disabled the firewall on his router and everything started working great. It then hit me and I was reminded of my windows days and struggling with Norton's Antivirus and how it's firewall always conflicted with any other firewall in use. Anyway, I had the UFW firewall installed and active so I just disabled it (because the firewall in my router is much better), rebooted, and now everything is purring like a kitten. Problem solved:-] Thank you very much for your time BkkBonanza, and hopefully these rookie mistakes of mine will become fewer and further between!

---

### Post by rainbowagent7 on 2011-03-18
Looks like you beat me to the reply. I'll take all of that into consideration as well, we have three computers going pretty much all of the time (which by the way were shut off while I was troubleshooting the bandwidth) and my girlfriends son downloads torrents all the time. I've been trying to figure out what protocol torrents were under so I can limit or block them, thanks.

---

### Post by rainbowagent7 on 2011-03-18
p { margin-bottom: 0.08in; }  Me again. I wanted to add something to this because I found another culprit to my slow connection. After I disabled the firewall everything ran better, but it was still lagging. So I dug a little deeper, this time narrowing things down to a problem I just started having with Adobe Flashplugin. When I opened up my System Monitor I noticed two processes that were using between 80 and 100% of both of my CPUs, red flag! Anyway, I stumbled upon someone with the exact same issue, and after reading how he had success killing the processes, I did the same, with identical results. Killing the processes put my CPUs back at their optimal levels. I assumed it was due to my Flashplugin because my system generally runs like a well oiled machine, and it is the only thing I've received an error on lately. I also noticed in the monitor that the process "plugin-container" was reading 10% CPU, and it usually doesn't so I left system monitor up (noob note: right click on the header for System Monitor and click "always on top") and opened Firefox >>> Tools >>> Add-ons >>> Plugins,  went immediately to the Adobe Flashplugin, disabled it, and the Plugin Container dropped to zero. I re-enabled it and the CPUs went crazy again, I also disabled several other plugins to be sure it wasn't my imagination playing tricks on me, and it wasn't. So I wound up installing (Shockwave Flash 10.3 d180) and everything seems golden with very little lag. Apparently These problems came about with my last update, and it seems there have been many instances of this; I hope this info helps someone with the same issues. 

Oh, P.S., I'm sorry I didn't take very good notes, otherwise I could have provided the names of the two processes draining my CPUs and also where I obtained Shockwave, but I'm learning:-]


                                                                                                                                                  :guitar:

---

