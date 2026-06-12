---
title: "PVR350 no channel change"
date: 2008-05-14
forum: Mythbuntu
---

### Post by HainjeDAF on 2008-05-14
HI every one,

I recently upgraded my server to (k)ubuntu Hardy.
I did a full rebuild from scratch.

Also I installed Mythbuntu to use it as master back-end.
I have:
AthlonXP 1700+
Hauppauge PVR350
3Ware Escalade 8505 raid.

The Hauppauge card workd if Io:

>ivtv-tune -f 800
>mplayer /dev/video0

I get to see and hear Discovery Channel.

However, if i start the front end
I get static and cannot change channels...

If I have Mythtv-frontend running and I do

>ivtv-tune -f 800

on a terminal,I _do_ get discovery channel in Mythtv
But still can't change channel

Anyone?

Regards,
marout

---

### Post by volkswagner on 2008-05-14
Did you follow all steps in backend setup?  Did you perform a channel scan in backend?  Can you post /var/log/mythtv/mythbackend.log and /var/log/mythtv/mythfrontend.log?

---

