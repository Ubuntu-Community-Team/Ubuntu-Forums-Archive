---
title: "Belkin USB wireless"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by `GooZ´ on 2005-12-31
I bought a Belkin stick, because the wiki told me I just had to plug it in and it would work. Well, it didn't. So I installed the Windows drivers with ndisgtk. This wouldn't work, so I runned it in terminal mode so I could see what was wrong. It seemed it already found some kind of 'alias' and the ndis module couldn't be inserted. This was, according to the terminal output, because of a lack of privileges. But since ndisgtk is runned as su (via gksudo) I wouldn't know what the problem is.
Please help me! I want to show off this new year's eve with Ubuntu... Thanks

---

### Post by djgenesis on 2005-12-31
Have you tried NDISwrapper? It worked for me on my wireless usb. I had some instabilities but at least i could test it worked ok. 

There's a nice HowTo [Here]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking")

See if it works for you 

Genxx

---

### Post by `GooZ´ on 2005-12-31
ndisgtk=ndiswrapper, so this doesn't solve my problem!

---

