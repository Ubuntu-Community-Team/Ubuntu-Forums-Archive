---
title: "NFS over Hamanchi or another solution?"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by davesmivers on 2009-05-15
I do IT support for a local company, a few months back I setup a 1TB NFS share on an ubuntu rig accessible from 2 mac and 3 windows machine on the local network. It's faster than samba and is very stable. Cheers guys - great support on here :)

They now want this NFS share accessiable from a couple of remote XP machines - one at home and one in an their store house. What's the best way of sharing this???

I'm thinking (so i can add more machines in the future ) hamanchi for linux. Does NFS work across himanchi? I can't see why it shouldn't? Alternatively am I barking up the wrong tree? Is there another simpler way? Secure FTP crossed my mind but i'm not sure. Any other Ideas? Thought about VPN but they are being tight and don't wont to go and buy new VPN routers.

Cheers in adavnce,

Dave

PS They have a static IP

---

### Post by davesmivers on 2009-05-16
*bump :/

---

### Post by davesmivers on 2009-05-17
Does nfs work over hamachi then? Just so i don't start summin I can't finish.

---

### Post by superprash2003 on 2009-05-18
yes it should , havent tried it personally though, but if you configure NFS to listen to the hamachi interface and access using the hamachi ips 5.x.x.x , then it should work..

---

