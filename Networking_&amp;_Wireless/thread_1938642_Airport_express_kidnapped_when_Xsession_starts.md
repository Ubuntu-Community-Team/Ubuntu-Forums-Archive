---
title: "Airport express kidnapped when Xsession starts"
date: 2012-03-10
forum: Networking &amp; Wireless
---

### Post by kamaron on 2012-03-10
Hi all,

I have struggling with a weird issue with my Airport Express.
I have it connected wirelessly to my network and since some time ago I was unable to srtream to it from my Mac.
It always said that the AEX was being used by another computer and I thought that it was a problem with the iMac itself.
Some days ago it was showing the error message when I restarted my Ubuntu machine and the iMac started streaming suddenly.
After some tests, I have concluded that it is when the Xsession.
I alsways start the machine in text mode.
If the iMac is streaming at startup time, it works with no problem until I start the Xsession.
Upon completion of the startx command, the iMac stops streaming and the Airport Express is unavailable for the iMac.
Any hint at least on how to aproach the problem?
Thanks for your help

---

### Post by kamaron on 2012-03-10
I am replying to myself and I hope this can be useful for others.
The problem was caused by Pulseaudio.
Checking the "Make discoverable Apple AirTunes sound devices available locally" makes Pulseaudio to take control over Airtunes even though it is not using it.
Unchecking it solved the problem.

---

