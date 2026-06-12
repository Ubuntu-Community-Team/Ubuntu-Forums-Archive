---
title: "Novatel Merlin S620 EVDO Card"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by blather on 2006-06-04
Hello.  I am having some problems getting my Novatel Merlin S620 EVDO card to connect.  I've tried using both the pppd and wvdial methods outlined in other posts in this forum.

This is what happens using the wvdial method.  Using tail outputs nothing from wvdial, so I can't offer much help there.

```
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
```

And so on.

This is what happens using the pppd method.  The following is what tail outputs:

```
Jun  4 02:59:03 ubuntu pppd[7120]: pppd 2.4.4b1 started by ubuntu, uid 0
Jun  4 02:59:04 ubuntu chat[7121]: expect (^M)
Jun  4 02:59:34 ubuntu chat[7121]: ^M
Jun  4 02:59:34 ubuntu chat[7121]:  -- got it
Jun  4 02:59:34 ubuntu chat[7121]: send (TIMEOUT^M)
Jun  4 02:59:34 ubuntu chat[7121]: expect (120^M)
Jun  4 02:59:34 ubuntu chat[7121]:
Jun  4 02:59:34 ubuntu chat[7121]: NO CARRIER^M
Jun  4 03:00:19 ubuntu chat[7121]: alarm
Jun  4 03:00:19 ubuntu chat[7121]: Failed
Jun  4 03:00:20 ubuntu pppd[7120]: Exit.
```

Frustrating, to say the least.  Any insight that could be offered on this issue would be greatly appreciated. :)

---

### Post by blather on 2006-06-04
I fixed it.  It was stupidity on my part. :D

---

### Post by malacandra on 2006-06-13
Um...could you share what it was you fixed? It might benefit others (like me) who are having trouble.

Thanks!
Mark

---

### Post by blather on 2006-06-14
Yes, certainly.  I apologize for not doing so.  Basically, I scoured the internet for people who have gotten theirs to work and combined their steps into one set of actions which got me going.  Here is an outline:

First, go to [http://www.cs.drexel.edu/~kfu22/evdo/](http://www.cs.drexel.edu/~kfu22/evdo/)
Most of his steps are accurate.  Make sure to download the files that he offers.  They're the important part.

The first thing I did was, in Windows, opened the Sprint PCS connection manager.  (Other services using this card should run the same software.  It'll just be titled differently.)  Go to the menu, and then Device Info & Diagnostics.  In the ensuing dialog, verify your username.  I'm not sure of capitalization is a factor, but I used what was presented just to be on the safe side.

Edit the sprint file from the above site to include the username you just found.

From that point, load up Ubuntu, and do **cp sprint* /etc/ppp/peers** on those files.
Next, **cd /etc**, and do a **sudo wvdialconf**.  Ubuntu will detect the EVDO card, and mount it appropriately.  It should be /dev/ttyUSB0, however if it isn't, you will have to edit your sprint file again to reflect the difference.

One final bit of editing to the sprint file is to add the following line.

**lcp-echo-failure 0**

These EVDO cards don't use the same format as a dialup modem, and so it is likely to disconnect you after 2.1 to 2.6 minutes without adding that line.

From there, simply **sudo pppd call sprint** and you should be ready to go.  Let me know if this helps, or if you need some more assistance.

---

### Post by kouakou on 2008-02-08
that worked but holly macaroni .....ubuntu is not for some one who has been using windows all their life...first I could not copy files to the specified folders....something about me not being the owner of the computer.....took me about 2 weeks to figure that one out .....then a whole four days to get this working .....I would give up but my girl friend has my att card which works on ubuntu and I cannot be on the road without the internet.....well I am very grateful for ur help......again thank u

---

