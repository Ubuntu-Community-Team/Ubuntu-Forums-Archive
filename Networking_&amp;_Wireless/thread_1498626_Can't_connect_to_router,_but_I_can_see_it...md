---
title: "Can't connect to router, but I can see it..?"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Fittersman on 2010-06-01
Hi,

Basically I am unable to connect to my WPA secured wireless router even though I know for sure I am entering the password correctly. I'm actually having a similar problem on my desktop, but thankfully on windows 7 you are able to use the push button method so I can at least connect to the internet there. 

There are about 6 computers in my house, 4 of which seem to have no issues connecting to the wireless router. The remaining 2 computers (mine of course), are unable to connect to the wireless router. The only way I can get internet is on my desktop under windows 7 using the push button method.

When my laptop was running debian, I had no problems connecting to the router. Only now that I am running ubuntu 10.04 it is all of a sudden having the same problem as my desktop and unable to connect. Both of my computers are able to see the wireless network, but for some reason they just can't get a connection.

Does anyone have any ideas as to why these two computers seem to be unable to connect to my router, even though I know the passkey is being typed correctly?

---

### Post by Fittersman on 2010-06-01
This information might also be helpful to some:

Wireless router: D-LINK DIR-628
Wireless card (desktop): Linksys WMP-600N Wireless N
Wireless chipset (laptop): Broadcom BCM4322 (I know, not the best choice for linux. However, I do have the drivers all installed and working)

Also, if I turn WPA off, I am able to connect to the router without problems.

---

### Post by Fittersman on 2010-06-04
OK.. So apparently my laptop works no problem with WEP encryption. Now, I could stick with WEP, but then I can no longer use wireless N.. Which is a problem for router range (as far as I'm aware). I have not yet done any serious testing, but I can only assume I'm going to be getting weaker signals when using  wireless G instead of wireless N, and that is not a good thing because I play online games on a computer which is of moderate distance from my router.

So, there is clearly a problem with the encryption somewhere, but I don't understand where the problem would be.

---

### Post by Fittersman on 2010-07-27
Just so there is an answer to this post, I ended up replacing the router. I now run on WPA2 personal with AES encryption and there are no problems. It's the same router, there just must have been something wrong with the old one (it was doing other weird things too).

---

### Post by Iowan on 2010-07-27
While you're at it... [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ;)

---

