---
title: "Recording Issues and an unhappy wife"
date: 2012-10-31
forum: Mythbuntu
---

### Post by TheFuzz4 on 2012-10-31
Hey Everyone,

First off thank you all for your help in advance with this.  So here is my dilema.  My myth box is not recording shows if liveTV is left on, on a front end somewhere in the house even if no one is watching the TV.  The backend says that its recording the show but it actually isn't.  Then after the show is over with the backend still reports that its recording the show.  The recording schedule also will get all out of whack when this happens as well with the backend still showing upcoming recordings from 3 days ago or however long.  The only way that I've found to fix this issue is to restart the backend.  

My backend is just a HP Proliant DL385 G1 in my crawlspace with the tuner card. 
The Frontends are various PCs.  Everything is running 12.10.  Thanks.

---

### Post by TheFuzz4 on 2012-10-31
I apologize as I just stumbled across this as a known issue.

---

### Post by Rotak on 2012-10-31
Can anybody tell me, if this issue still present in 0.26?

---

### Post by nickrout on 2012-10-31
> **TheFuzz4 said:**
> I apologize as I just stumbled across this as a known issue.There is a setting to time out livetv if nothing happens (ie no remote presses etc) after as period of time. Set that and it will help.

Other than that you probably need more tuners :)

---

### Post by TheFuzz4 on 2012-11-01
Do you by chance know what setting this is?  Thanks.

---

### Post by nickrout on 2012-11-01
> **TheFuzz4 said:**
> Do you by chance know what setting this is?  Thanks.

Setup|Video|Playback, 1st page.

---

### Post by anonymousdog on 2012-11-27
> **Rotak said:**
> Can anybody tell me, if this issue still present in 0.26?
I see **some** evidence that ticket #10489 was "fixed" but none that the fix was committed (at least to 0.25.x code).  It **may** be fixed in 0.26.  It'd be nice to know.

It'd also be awesome to know whether they've fixed the zero-byte recording problems with PVR-150, -350 and -500s.  (See [http://code.mythtv.org/trac/ticket/10732](http://code.mythtv.org/trac/ticket/10732).)

---

