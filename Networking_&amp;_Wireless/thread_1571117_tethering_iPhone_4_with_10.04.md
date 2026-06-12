---
title: "tethering iPhone 4 with 10.04"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by Wayne0188 on 2010-09-09
i had tethering workign perfectly with my iPhone 3G, but then i upgraded to an iPhone 4.
now i cant tether anymore, and i cant find any help on this, please help.
 
when i connect to my computer, i can use rhythem box to view/play music on phone, and sync.
 
the auto eth1 thing does not kick in, I even tried toggleing the tethering on and off, no go.
 
tethering works fine on any windows computer though, and since I hate windows, I would love to get this working in ubuntu, so if you have any ideas, please share.
 
thank you in advance.

---

### Post by Wayne0188 on 2010-09-10
Bump.
Does anyone know a solution?

---

### Post by lukeiamyourfather on 2010-09-10
Wi-Fi tether maybe?

---

### Post by Magbed on 2010-09-15
I have the same troublem was working flawlessly on my iphone 3g with some guy homemade drivers but i cant fins any solution on the inet for tethering through iphone4. Anyone has any idea? Thanks

PD: Wi-fi isnt an option since its an old computer without wifi connectivity

---

### Post by Magbed on 2010-09-15
Think i found some sort of fix in this post but i dont know how to apply it anyone can help?
[http://github.com/rigtorp/ipheth]("http://github.com/rigtorp/ipheth")


Thanks

---

### Post by samuel.faith on 2010-09-20
> **Magbed said:**
> Think i found some sort of fix in this post but i dont know how to apply it anyone can help?
[http://github.com/rigtorp/ipheth]("http://github.com/rigtorp/ipheth")


Thanks

I have iPhone 4 and also facing same issue as you. I will test this out and will update you with my findings.

--Sam

---

### Post by @dministrator on 2010-10-01
Update Guys:

I just plugged in my iphone 4 and internet tethering just started working. I did recently install some updates including a new kernal image so that may have something to do with it. Also, I have tried to get it to work by using various methods described via google searches.. so perhaps one of those packages were updated recently too. 

The point is, if you have an iphone 4 and you with to use internet tethering with your notebook or other device then I suggest you update via the update manager, plug it in and give it a try!

---

### Post by mybunche on 2010-12-24
It does work with Ubuntu 10.10 (with latest updates as of 24 Dec 2010) and iPhone 3G with iOS 4.2.1. 

Enable USB tethering on the iPhone, plug it into your Ubuntu machine, 5 secs later you will have connection. It actually shows as a wired network connection, but is perfect and speed is great.

NB: I did try this a month ago and it would not work. I think I remember some updates that come down a little while ago so that probably fixed it.

---

### Post by kdi on 2011-01-25
Fortunately, my iPhone 4 with iOS 4.2.1 just work. I'm tethering it now to post this exciting news.

1) Pair my iPhone 4 bluetooth with my Dell Studio 1435

2) Click on the NetworkManager icon n select a weird internet connection name

3) Guess what, enjoy my tethering...:popcorn:


Note: I don't get usb tethering working though.

---

### Post by Heero_Yuy_X on 2011-09-10
There is a package "ipheth-utils" in the default Ubuntu repositories having a description of :
"USB tethering driver support utilities for the iPhone" .

I guess you could try installing that and just plug in the iPhone and see how it works..

---

