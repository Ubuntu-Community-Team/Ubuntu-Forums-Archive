---
title: "Can't get IP Masquarading working"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by Que914 on 2012-01-11
Hello.

I'm attempting to setup my home network such that I can remote into my home box when I'm out.  I've setup my router with the appropriate port forwarding but I can't seem to get past the firewall.  

I've followed the firewall tutorial [here]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html"), but I'm still getting blocked when I attempt to SSH into the box.  I see the blocking occurring as such in the log:

> 
kernel: [69242.788422] [UFW BLOCK] IN=eth0 OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:00:00 SRC=208.54.40.226 DST=192.168.0.105 LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=53381 DF PROTO=TCP SPT=64071 DPT=22 WINDOW=5840 RES=0x00 SYN URGP=0 
 

When I specifically allow from 208.54.40.226 I can ssh in just fine so I know it's getting at least that far but I can't find what I'm missing.

Any help would be greatly appreciated.

Thanks.

---

### Post by Doug S on 2012-01-11
I do not see where you are allowing port 22 in your INPUT chains (Maybe I missed it).
Once you get it working you will have hackers beating upon your system, perhaps review [this thread ]("http://ubuntuforums.org/showthread.php?t=1903537")and its embedded links.
 
Hope this helps.

---

### Post by jmate24 on 2012-01-11
i heard that you cannot spoof or mask your ip because it is illegal but you can set your computer behind a linux firewall pc and that pc then becomes your ip and gateway to the internet. i have also heard that it is also best to have a "dummy" computer that has windows and BlackICE installed that way if some one hacks your network then they more than likely will go for the dummy windows pc than your linux PCs.

here's where you can get BlackICE:
[http://download.cnet.com/BlackICE-PC-Protection/3000-2092_4-10316410.html]("http://download.cnet.com/BlackICE-PC-Protection/3000-2092_4-10316410.html")

Happy Computing...

---

### Post by Que914 on 2012-01-12
I don't actually have port 22 open to the outside world, I have it setup on my router to forward from another port.

As to the allows, I have a an 'allow from 192.168.0.0/24' in my ufw firewall rules.

---

