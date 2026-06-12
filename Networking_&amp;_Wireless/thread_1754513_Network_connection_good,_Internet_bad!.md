---
title: "Network connection good, Internet bad!"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by theller on 2011-05-10
So here is a bizarre problem. On a school network the Windows and Mac computers connect to the internet with no problem. The Ubuntu(10.04) computers are connected and work on the internal network but have major issues going out of the building. I can get to one or two webpages to open and the connection dies...Server not found. Ping within the network and there are no lost packages, if I ping outside many lost packages. We are using SonicWall and think it could be blocking...but why only Ubuntu?

This is the same behavior for Firefox and Seamonkey. It's also the same for the thin/fat clients and standalone units. I did try a fresh install with no effect. The internet actually works on the one machine with ubuntu 9.10. I brought a machine home and it connected to the internet with no problem. 

Two things I can think of that would of caused this are:
1- we keep getting windows about missing applets, someone may have clicked delete
2- I connected a server to run fat clients w/ LTSP and discovered my server and the schools were handing out the same ip's.

---

### Post by theller on 2011-05-10
New discovery...something is handing out ipv6 addresses. Is that bad?

---

### Post by theller on 2011-05-18
Someone plugged a home wireless router into our network. When we realized, I walked the halls until I found a signal I didn't recognize, looked in that room, found the router, killed it, and our problems were solved.

---

