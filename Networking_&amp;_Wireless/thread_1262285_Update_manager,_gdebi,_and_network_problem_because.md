---
title: "Update manager, gdebi, and network problem because of an old proxy"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by suckmypianist on 2009-09-09
WARNING: This post WILL be long. I just want to be as specific as possible so as to get the most accurate answer. So just stick with me for a bit :]

Hi, I'm slightly new to Ubuntu and I need the help xP so thanks in advance. I had Intrepid [8.1] Desktop Edition for maybe a couple months until about a week or two ago. Now I have Jaunty [9.04] Desktop Edition. I recently ran into a problem though... I was trying to connect to my school's network (which uses a proxy and username/password to connect to the Internet) I connected just fine to the Internet when using Firefox, but when I tried to install a .Deb package of AWN, gdebi couldn't install it because it couldn't connect through the proxy. So I went to System menu -> Preferences -> Network Proxy. Network Proxy Preferences opened up and i clicked "Manual proxy configuration" and entered in to the "HTTP proxy:" text box "ehs-proxy.sau16.ad" (the proxy my school uses) and in "Port:" i entered "3128". I clicked "Apply System-Wide..." then clicked "Close". I tried gdebi again and it still couldn't connect, it said it needed authentication. So I went back to the proxy settings and beside the http proxy and port for it it says "Details" I clicked it and entered in my authentication user and pass. I made surethat I entered them right. Needless to say... that didn't work either. Now I'm getting slightly tired of typing so I'll hurry this up. I then tried the automatic proxy configuration... still didnt work. i gave up on that after searching for answers and about 1 and 1/2 to 2 hours of trying... but the real problem is now im back at my house and im trying to install a few things and its trying to connect to my schools proxy... i've gotten rid of all the proxy settings and clicked apply system-wide (ive done this quite a few times...) yet nothing seems to be working... gdebi and "[Update Manager]" keep trying to connect to my schools proxy. its starting to piss me off and i REALLY dont want to re-install Ubuntu. if anyone can help PLEASE just try. 
thanks in advance
~Jeremy

---

### Post by spykEee on 2009-09-17
Wow. I have essentially the same problem. So sad for both of us that no one has responded:confused:

OK, maybe I didn't have the same problem. The clue to my solution was in your post: I had gone to System/Preferences/Network Proxy and selected "direct connection, but I failed to click on "apply system wide. That seemed to do the trick.

---

