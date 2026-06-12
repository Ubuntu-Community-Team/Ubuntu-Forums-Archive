---
title: "can't get to website, did I get blocked?"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by revenant138 on 2010-11-25
Hi all,

I'm trying to get to forex.com. This was working fine until about two days ago. None of the 3 computers in my house can get there (win 7, win xp, ubuntu). I can do a nslookup on it from my local DNS and one of Google's (8.8.8.8), and I get the same IP addresses. If I try to go there by the IP address, I get that the server denies me permission.

I did a traceroute, and I correctly can get there:
> revenant@gibeon:/etc$ traceroute forex.com
traceroute to forex.com (74.217.51.67), 30 hops max, 60 byte packets
1  192.168.1.1 (192.168.1.1)  7.644 ms  7.915 ms  8.201 ms
2  * * *
3  ge-9-11-ur01.maplegrove.mn.minn.comcast.net (68.85.166.65)  18.569 ms  18.954 ms  19.902 ms
4  te-8-3-ur02.maplegrove.mn.minn.comcast.net (68.87.174.50)  19.449 ms  20.295 ms  20.706 ms
5  te-2-1-ur01.hamlake.mn.minn.comcast.net (68.87.174.62)  21.090 ms  22.706 ms  23.088 ms
6  te-8-3-ur02.hamlake.mn.minn.comcast.net (68.87.174.66)  22.232 ms  11.073 ms  13.930 ms
7  te-2-2-ar02.roseville.mn.minn.comcast.net (68.87.174.69)  14.405 ms  16.032 ms  16.247 ms
8  te-1-1-0-4-cr01.chicago.il.ibone.comcast.net (68.86.95.5)  25.074 ms  25.540 ms  26.593 ms
9  pos-1-8-0-0-pe01.350ecermak.il.ibone.comcast.net (68.86.87.166)  32.162 ms  33.780 ms  35.026 ms
10  208.178.58.73 (208.178.58.73)  30.569 ms  31.652 ms  25.256 ms
11  67.17.192.54 (67.17.192.54)  57.523 ms  57.563 ms  56.991 ms
12  border1.pc2-bbnet2.nyj001.pnap.net (216.52.95.73)  57.102 ms  52.212 ms  55.903 ms
13  74.217.51.67 (74.217.51.67)  53.192 ms  54.876 ms  54.269 ms
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

I cannot get any response to ping via IP address or hostname. I had my dad who lives across town give it a try, no problems there. I'm almost wondering if they blocked my IP for some reason (their website hasn't played real well with linux, tends to log me in and out frequently, maybe I got blacklisted? It also will say I'm logged in but only give me like half the options, then if i logout and back in its fine. Could it have been flagged as suspicious behavior?)

Later...
I'm at his house for thanksgiving now, I can get to the site directly with my netbook. I can't access the site directly by IP but I can by the name. When I use the IP it says > 403 - Forbidden: Access is denied.
You do not have permission to view this directory or page using the credentials that you supplied.

Anybody have any ideas?

---

### Post by chili555 on 2010-11-25
My thinly informed guesswork is that the only credentials I think you may have provided are cookies. I suggest you go to Edit > Preferences > Privacy > Show Cookies. Search for forex.com and delete them all.

You will have to supply your username and password again. 

Are you long on the yuan?

---

### Post by psoup1965 on 2010-11-25
If you get a 403 and there are no user accounts etc... that is you do not have to enter a member info then the issue is the website and there is nothing that you can do to fix it.

But if it makes you feel any better about if th esite is up or down right now I am there and it works.

Be sure you are using [http://www.forex.com](http://www.forex.com) as your entry point and not a specific shortcut to somewhere AFTER you need to enter your account information.

---

