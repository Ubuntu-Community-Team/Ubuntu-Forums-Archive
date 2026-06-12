---
title: "Ubuntu machine sucks up my bandwidth simply by being on"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by jgk483 on 2011-06-10
I have an ubuntu machine connected to my network which is used as a Minecraft server, storage, and a subsonic server for music.  For the most part, the only person using these services, especially during downtime, is just me at home.

Which is why I'm surprised that 2-days ago I detected that my network was being slowed to a crawl.  

There I found that the ip connected to my ubuntu was moving around 170,000 kb on my Netlimiter 3 program.  

I have no idea why that is, I closed my ports that were forward for the ubuntu servers, but the bandwidth keeps leaking.  Disconnecting the network from the ubuntu computer or turning off the computer stops the odd downloading and uploading.

Not sure what is the problem.  If anybody would have any information of what I can check or shut down in Ubuntu, please let me know.  I'm fairly a beginner to the OS, but haven't been able to find a similar problem on this forum.

---

### Post by jgk483 on 2011-06-12
Is there no solution to this?

---

### Post by superduperlinuxperson on 2011-06-12
does your network have a wep or wpa key?

---

### Post by jgk483 on 2011-06-12
Yes, a WPA.

As said before, the bandwidth leeching comes only from my Ubuntu computer, and not my router or network itself.  I have a Windows Computer as well that is on at all times, and a quick run through Net Limiter shows that when it is inactive, it isn't pulling any kind of bandwidth.  

The Ubuntu machine, on the other hand, is downloading a ton.  As if it was running a torrent... even if it's simply on and inactive!

---

### Post by superduperlinuxperson on 2011-06-13
here is what i think your problem is:
windows does not "hog" wireless, unlike apples devices. same thing happens too our computers; turn the iphone off, wait a couple of minutes, and our windows wireless is working perfectly. turn it on however an it immediatly starts going down. i think ubuntu also does that because the bars on my computer dont move, but the ipad or iphones does.

---

### Post by jgk483 on 2011-06-13
I don't think I follow you.  I have an android phone always connected to my router, and it's not pulling in 170,000 kb like when I connect my ubuntu to my network. 

Also this phenomenon has been going on since last weekend, not when I first installed ubuntu onto this computer.   

The reason I found out that the Ubuntu machine was sucking bandwidth was because I was having trouble using the Internet, as if someone was torrenting something over my wireless.  Turning off the ubuntu machine, or unplugging it from my network, solved this problem.  

Is there a way to find out which process on ubuntu could be utilizing the Internet at such a big rate?

---

### Post by rivode on 2011-06-14
I'm not sure if it will tell you which process is using the data, but "iftop" can tell you the speed of individual connections.  Once you work out which ports are involved, "sudo netstat -n -p" (I think) will tell you the process that is using that port.

---

