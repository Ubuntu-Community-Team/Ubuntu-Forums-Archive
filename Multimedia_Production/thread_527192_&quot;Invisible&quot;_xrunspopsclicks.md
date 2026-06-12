---
title: "&quot;Invisible&quot; xruns/pops/clicks"
date: 2007-08-16
forum: Multimedia Production
---

### Post by user_name_ on 2007-08-16
I have som interest in music, and I thought it could be fun composing in linux. Therefore I got ubuntu studio, which included some of the programs I would like to use. (Rosegarden and some softsynths.)

Right now, I'm running Ubuntu Studio patched with the realtime kernel found here in the forums, but I'm still not satisfied. I have configured jack so that the latency is 10 or 20 msec, which is the lowest "stable" settings I can run it in.

At these settings, no significant xruns show up in jack. (Except sometimes when I start the softsynths, but I guess those doesn't count.) But even if jack keeps going along happily, I still hear some stuttering, pops and clicks under playback. Also, I get some strange pops/clicks in XMMS too, each time it changes tracks. I don't think there is any connection there, but I thought I'd mention it anyway. 

Anyone who has experienced a similiar problem?


I'm sorry I can't specify more at the moment.

My hardware:

M-audio Revolution 2496
AMD64 4000+
2gb RAM
Seagate 7200rpm 500gb disk
Geforce 8500
Asus M2N -E SLI motherboard

---

### Post by westli on 2007-08-16
Your latency only needs to be low if your are recording and trying to monitor what is being recorded in real time and through the computer.  If you can work around that by listening to the instrument directly, or if you are working with loops or composing with the mouse in the piano roll view, you don't need the lowest latency possible.

Try increasing latency 10 msec at a time until the pops & clicks disappear.  Those are usually caused by too-low latency.

:guitar:

---

