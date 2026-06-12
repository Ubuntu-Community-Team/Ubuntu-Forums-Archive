---
title: "Music shares from a MacBook Pro"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by Lorthirk on 2009-09-02
Hello all. First of all, sorry if I'm writing in a wrong session... But this seems to be the most relevant in which to ask for help.

I have a MacBook pro with Snow Leopard on it, and a fairly big music collection (about 10 GB). I'd like to share my music to Rhythmbox on my Ubuntu desktop.

Moreover, by having an XBOX 360, I have a little utility called Connect360 which I use to share the collection to the XBOX 360 via UPnP/DLNA; although the XBOX can see the music perfectly, it seems that Connect360 it's not a "standard" DLNA server.

Now, the obvious question is: what can I use to achieve my target?

---

### Post by tgalati4 on 2009-09-02
If you put Ubuntu on your macbook pro and run rhythmbox, it will probably show the music shares.  Or get an iMac and run iTunes and your iTunes shares from your macbook pro will probably show up.

---

### Post by Jota37 on 2009-11-21
I have exactly the same situation, but it is my girlfriend's Macbook Pro (also for her XBOX 360), and that's why I landed here... ;) It does have iTunes installed, and set up to share. My Ubuntu installs can see the share, but when I click on them it gets forever stuck in "Retrieving songs from music share", and never does.

I've read, on other forums, people complaining about this. Someone said that it is an iTunes 7+ problem -- encryption to ensure that only other iTunes clients will be able to read the library, and that iTunes (in their case, but not in mine so far) can read other programs libraries but not vice-versa. I don't know if that it is indeed the case, but considering how evil Apple can be as control freaks, it sounds plausible. Actually, make that likely instead of plausible.

Anyway, right now what we have done to solve the problem here is use regular OS folder sharing, and then I read from the folder (we set it up as SMB on the Mac, and the Ubuntu machine immediately saw it in Nautilus).

Not ideal and elegant, but it does the job.

---

