---
title: "Remote problem - Window losing focus?"
date: 2009-10-28
forum: Mythbuntu
---

### Post by johnvan on 2009-10-28
I'm having an intermittent problem with my remote. It could be 2 keypresses or 50 keypresses , but eventually mythtv stops responding.
My remedy is to run downstairs and log in with VNC, clck on the mythtv window and I'm back in business.
It seems to me like that's a problem with the window losing focus. Any ideas?

Thanks

---

### Post by klc5555 on 2009-10-28
> **johnvan said:**
> I'm having an intermittent problem with my remote. It could be 2 keypresses or 50 keypresses , but eventually mythtv stops responding.
My remedy is to run downstairs and log in with VNC, clck on the mythtv window and I'm back in business.
It seems to me like that's a problem with the window losing focus. Any ideas?

Thanks

Sounds like some program has opened underneath mythfrontend and has taken focus. Find out which one it is and prevent it from opening.

When I first updated to 9.04, a frequent culprit for this was the update manager. Setting it not to check for updates automatically was the easiest solution.

---

### Post by johnvan on 2009-10-28
I disabled update manager also when I first set it up. If I exit mythtv I don't see any windows or programs open.

---

### Post by azmyth on 2009-10-28
I ran into this problem as well. Just not sure if it was a window focus issue until I read your post since restarting gdm resolved the problem for me. The downside is if you're using irexec I had problems with restarting gdm killing irexec.

---

### Post by johnvan on 2009-10-28
I'm using a straight mythbuntu installation on my frontend.  It's xfce rather than gnome, unless I'm confused.
Did you resolve the issue 100% or do you restart gdm each time it freezes up.
I don't have a keyboard or mouse on my frontend so the quickest fix for me right now is with remote desktop. Log on/Click/Log out
I'd love to fix it once and for all, it's going to be tough to explain to babysitters how to fix the remote once it stops working, which it will.
It might not be the window focus, maybe I'm chasing up the wrong tree.

---

### Post by azmyth on 2009-10-28
I'm using xfce as well and when I read to do a service gdm restart it threw me as well. Just to make sure we're on the same issue. It would take a few days before my remote wouldn't control the frontend. I did a ircat mythtv and it was obviously getting the keypresses. I originally started out by adding the service gdm restart to my crontab and have it restart once a day early morning. I ended up moving to restarting lirc once a day. Both caused issues with irexec that took me awhile to resolve properly. Not sure if you're having the same issue as me though.

---

### Post by johnvan on 2009-10-28
Sounds like it's a different problem.  I start my frontend only when I need it so everything is restarted daily.  The remote always works on initial startup.  It just randomly fails later.
The nearest bug I could find is this: [https://bugs.launchpad.net/mythbuntu/+bug/421276](https://bugs.launchpad.net/mythbuntu/+bug/421276)

It's a little tricky to troubleshoot because as soon as I log in with VNC the remote starts to work again. I updated to the latest kernel.  I might try an older kernel.
I hate to mess around with LIRC because it took a while to get the remote setup in the first place.  
Thanks for your inputs.

---

### Post by azmyth on 2009-10-28
Yes, it looks like a different problem. May trying to ssh in to prevent logging in through VNC from fixing it.

---

### Post by johnvan on 2009-10-29
Weird thing, I had the remote fail on me again this morning after about an hour of working great.  This time I opened gftp and connected with SSH and it fixed the remote.

It kicks it back into the previous screen, it was playing a recording and as soon as I established the connection it stops the recording and puts it back to the recorded programs list and the remote works.

Possibly related, twice in the last week I've had the screen fade to black while watching a recording, I can see a mouse pointer and then the screen immediately comes back on its own.

---

