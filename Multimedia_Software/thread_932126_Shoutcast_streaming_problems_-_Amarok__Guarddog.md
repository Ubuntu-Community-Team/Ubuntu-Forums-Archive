---
title: "Shoutcast streaming problems - Amarok / Guarddog"
date: 2008-09-28
forum: Multimedia Software
---

### Post by eyads on 2008-09-28
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install libxine1-ffmpeg amarok-xine w32codecs libdvdcss2

After going through all the finger spaghetti above to listen to Shoutcast, I noticed that some Shoutcast streams still don't work, reporting something similar to this:[INDENT] Amarok > **Error Loading Media**

No suitable input plugin. This is often means that the URL's protocol is not supported. Network failures are other possible causes.

[http://64.71.144.178:8010](http://64.71.144.178:8010)[/INDENT]After playing around for a bit, I noticed different streams use different TCP ports e.g.:

7110
7290
7870
8004
8010
8020
8022
8090
9000

So with Guarddog, I tried setting the "**Random port range**" to 7000-9000.

Didn't work**!** Does anybody know why**?**

What I have now is a "**User defined port range**" 7000-9000 TCP (allowing data from "**Internet**" to "**Local**"), and that works.

I'm just worried about having such a big range of ports open,if somebody has another suggestion - I is all ears! :shock:

---

### Post by eyads on 2008-09-28
> ...
What I have now is a "**User defined port range**" 7000-9000 TCP (allowing data from "**Internet**" to "**Local**"), and that works.
...

Saying that, just listening on a stream on port 8010 seems to interfere with my browsing (?problems with cookies maybe?)  EEEEEELP!

---

### Post by drpyro on 2009-07-01
try this should install required codecs for amarok
```

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libxine1-ffmpeg
sudo apt-get install phonon-backend-xine
sudo apt-get install phonon-backend-gstreamer

```

:)

---

### Post by daniel-linux on 2009-07-13
create rules for the ports u need in guarddog under the advanced tab and then open them under the protocols tab

---

### Post by eyads on 2009-07-19
I found the problem, I tinkered too much in Guarddog and accidentally limited the "Random port range" too a small value, which ended up restricting Firefox browsing.

As for shoutcast, my incoming port range is now from 7000 - 9000, which is good enough for most streaming connections.

One question .. how do I mark this thread as [SOLVED] ??

Thanks people.

---

