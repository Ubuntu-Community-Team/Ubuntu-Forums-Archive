---
title: "Switched to Myth 0.25 PPA but myth-frontend is held back from upgrade?"
date: 2011-11-30
forum: Mythbuntu
---

### Post by kenyee on 2011-11-30
This seems a bit weird...I switched to the Myth 0.25 PPA (I'm on Mythbuntu 11.10) and everything upgraded except myth-frontend.

Anyone else hit this problem?  Seems strange for the dist-upgrade to switch everything else...

BTW, the 0.25 myth is a lot better...lets me set audio over HDMI on my sandy bridge IGP...

Specifically, what I see is this:
The following packages have unmet dependencies:
 mythvideo : Depends: mythtv-frontend (>= 2:0.25.0~master.20110608.5241f65-0ubuntu0mythbuntu3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Yet, according to apt-show-versions, mythtv-frontend is actually the 0.25 version:
mythtv-frontend/oneiric uptodate 2:0.25.0~master.20111130.dbd0cc0-0ubuntu0mythbuntu3

Looks like a mythvideo dependency error?


UPDATE: someone mentioned mythvideo isn't needed for 0.25 any more.
Still not sure why AVI files I stuck in that directory don't show up though in the media library menu though :-P

---

### Post by superm1 on 2011-12-01
Yeah mythvideo is no longer needed, it's functionality is built into the frontend with 0.25.  Are other files showing up and just not AVI's?

You might want to try running frontend from cmdline to see any errors.

---

### Post by kenyee on 2011-12-01
The big duhh was I didn't hit m to bring up the menu and do a "Scan for Changes".  I thought since mythvideo is no longer needed, this was done automagically on frontend restart...

Works fine now...thanks :-)

---

