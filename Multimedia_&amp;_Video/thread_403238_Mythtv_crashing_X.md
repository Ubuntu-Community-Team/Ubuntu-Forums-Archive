---
title: "Mythtv crashing X"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by scottishnarn on 2007-04-06
Mythtv suddenly developped a bizaar problem. In openbox which I usually use for running mythfrontend the x server is restarted when mythtv starts, when running gnome it will launch and run fine until I exit mythtv (or change a setting which automatically restarts mythtv) at which point it also restarts the x server. 

I think this has to do with a qt (or kde) upgrade since I have recently just done an update and the other minor issue below * (kept in a footnote to not distract from the important stuff). Is it possible to revert qt (& kde) librarys to older versions without reinstalling ubuntu? I had a look at synaptic but couldn't see any obvious ways of doing this. Or any other ideas about what to try or what could be causing this? 

I also tried backing up the database, deleting the database and seeing if I could run the mythtv-setup program again to check if it was a corrupted setting. But this didn't solve the problem and I had the same issues running mythtv-setup as I did with mythfrontend. I also get the same issue using two different users, so I don't think it's a configuration issue related to ~/.mythtv 

Thanks



footnote
=================
*There is a also a minor problem with gnome using a different user (but not the normal user I use for mythfrontend, interestingly) if I run mythfrontend the colours are all messed up (a bit like using the wrong palet with an 8 bit display, although I'm using a 24 bit display) apart from if I have another program on top (i.e. the terminal I launched mythtv from) but it goes back to colour messed up if I change the focus back to mythtv, apart from if I launch a qt or kde program before I launch mythtv (doesn't matter whether this program has been quit or is still running), then the colour is fine.

---

### Post by scottishnarn on 2007-04-07
As a follow up, I tried running mythfrontend as a new user to see if it was a settings issue, but I can't get beyond the initial screen to setup language and server address. It will let me put the data in but then it tries to restart mythfrontend which restarts X (even in gnome). When I log back in and try to restart mythfrontend it brings me back to the same config screen even although the correct data is remembered.

Any ideas anyone?

---

