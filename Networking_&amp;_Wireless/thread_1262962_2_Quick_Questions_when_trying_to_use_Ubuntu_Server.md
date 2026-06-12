---
title: "2 Quick Questions when trying to use Ubuntu Server 9.04"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by xMemphisx on 2009-09-10
I just setup my first home server using ubuntu, it's pretty ok so far, but i'm having some issues.

Number one, I have a PCI WiFi card, which is easily detected under restricted hardware manager and properly setup/installed... which is all well and fine, except i'm not using gnome, and i don't know how to get it setup so i can use it from the command line.

Number two, I setup "motion" with a webcam I have, but when i try and view the stream from any other machine from my local network ([http://ipaddress:8081](http://ipaddress:8081)) i get a cannot connect to server. I checked iptables using 

"iptables -L -n"

the port 8081 wasn't open, so i added it under INPUT (which didn't work, so i also added it under FORWARD and OUTPUT), but still no connection. I checked using "nmap" from another computer, and it outputs:

PORT STATE SERVICE
8081/tcp closed blackice-icecap

I used this method and forwarded ssh just fine, without any real issue, but i cannot get this working. Any help would be greatly appreciated.

---

