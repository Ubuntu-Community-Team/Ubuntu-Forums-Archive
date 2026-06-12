---
title: "Network manager"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by Chtfn on 2010-05-03
Hi everybody !

I was wondering: why the network manager isn't available from the beginning in Ubuntu Studio? I think this is a real problem for a lot of people who use a wifi connection to the Internet... It's the third time I install Ubuntu Studio, and the third time that I have to find all the packages necessary to install it, via another computer.

Is there any reason for that?

Another thing is the software center: it would have also been a good thing to install the software center from the beginning, it makes a lot of things easier.

Thanks for any answer. Hoping this gets fixed in the next release!

---

### Post by artard on 2010-05-03
I just completed my fresh 10.04 studio install and noticed the same thing!  Wired connection worked fine, but I couldn't locate an interface for connecting to a wifi router.

Searching these forums and elsewhere I found that we need to manually install network-manager... that did the trick for me, but I prefer the "wicd" utility so I'm using that instead now and it's working great.

- go to system, administration, synaptic
- search for "wicd" (or "network-manager" if you prefer, its the default for ubuntu 10.04)
- install and good to go! (assuming you don't need to configure your wireless drivers first, which I didn't)

---

### Post by trulan on 2010-05-04
Did they fix wicd?  I prefer it over network manager as well, but it had been failing to connect in Lucid, saying I had a 'bad password' (my password was correct).  So I removed it for the time being and went back to network-manager.  The bad password error may have only affected WPA secured networks.

---

