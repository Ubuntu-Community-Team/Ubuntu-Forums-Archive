---
title: "Networking problems"
date: 2012-09-29
forum: Networking &amp; Wireless
---

### Post by jasinthreenine on 2012-09-29
Hi Everyone. I just want to thank you in advance for reading my post. Here is the rundown. I have ubuntu 12.04 lts installed on an amd athlon IIx4 630. I have a gigabyte mobo with built in lan.

After installation internet worked just fine but now it doesnt. To my knowledge , I haven't installed any new software that would disable the internet from working. My internet connection icon is also missing from the bar at top of my screen. 

If I open a terminal and type "ifconfig" I get

inet addr:192.168.0.3 so i know the computer can see my router. I can even ping my router successfully from terminal; however, none of my web browsers will let me on to the web.  

I can use my windows 7 computer to log into my router. Then inside my router's configuration page I can see the devices connected to my router and I can see that my ubuntu computer is connected.  

Ive tried resetting router to factory defaults and I have restarted my ubuntu computer a few times and nothing. My ubuntu is a dual boot machine. It has mepis installed on a second hd and the internet works fine under the mepis OS. So i dont think it is a hardware issue. 

If i run ubuntu 12.04 live from dvd disc, i can get online. I just dont want to fresh install ubuntu everytime I get a problem. While Im fairly decent at figuring out windows, im not familiar with "under the hood" of linux. Sorry for the long story. I just wanted to give you as much info as a neophyte could.

---

### Post by uncaspi on 2012-09-29
Need more info. Is it cable or wireless connction? Btw missing icon point to a wrong driver for the card.

---

### Post by houstonbofh on 2012-09-29
To get a web page up, you need several things.  You seem to have connectivity locally.  Now how about remotely?

```
ping 4.2.2.2
```

That should come back OK.  If not try this.

```
route -n
```

The last line should have the IP address of your router as a gateway.

Next consider name resolution.

```
ping www.google.com
```

It should come back with a line like this, and then start pinging.

```
PING www.google.com (74.125.227.52) 56(84) bytes of data.
```

If that line is missing, it is a DNS issue.

This should get you started, unless it is a very odd problem.

---

