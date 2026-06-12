---
title: "Wired connection works for browsing, but not in games"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by mtfr on 2009-09-21
Hello, it's my first (whine) post here.

I'm still running Ubuntu Studio 8.04. Networking through my wired ADSL connection runs very smoothly for browsing and listening to net radio. But recently I installed 2 games: World of Goo (woohoo, nice one) and Heroes of Newerth (even better). The problem is, neither of them can connect to the internets.

World of Goo has this stage where you can see how tall towers the others have built. It simply says it can't connect; check the connection.

Now Heroes of Newerth can do *something* with the connection: when the game starts, it tells me what the latest version of the game is and what the installed one is. Then it would normally connect to download the latest files (like any MMO game) but it doesn't. Then, in the match lobby, it somehow can check from the server the fact that there is a number of X games currently in play. But it cannot do anything more than that: it cannot download a list of the games, therefore I can't choose to which to connect.

I am a relative noob and hence couldn't solve the problem by myself. I didn't even find what the problem is. I have already searched about firewalls and found a reference to ufw. I did disable ufw (I think it was already disabled since Ubuntu Studio installed) and I can check its status and it says that it's not running, so I can't imagine what the problem is.

I don't think it's because of my ADSL modem/router, because I run a dual boot with Windows for games, and for years now I didn't have any Windows game blocked/filtered.

Thanks for whoever may have any idea.

---

### Post by mtfr on 2009-09-22
I'm not sure if this practice is hated here, but here goes:

Up (for my thread, because I found no solution) :)

---

### Post by mtfr on 2009-09-27
Any idea? Where can I start looking into this?

---

### Post by mtfr on 2009-09-30
I am sure this is not because of my router, since it works in Windows... that's the only clue I have so far.

---

### Post by mtfr on 2009-10-03
I solved the problem!!!!!!!!!!!!!!!!!! Oh happy day!

When installing the games, they somehow were created with root ownership. I just had to:

```
sudo chown myuser.myuser gamedir -R
```

And now they can connect to the internets properly. Weird problem anyway. Hope this will help someone.

---

### Post by borisz264 on 2009-10-14
I'm having the same problem connecting with the world of goo linux port on Jaunty. Changing the ownership in the game directory (in /opt) changed nothing. Any suggestions?

---

