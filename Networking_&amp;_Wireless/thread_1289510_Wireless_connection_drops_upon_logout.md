---
title: "Wireless connection drops upon logout"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by ff8jake on 2009-10-12
Hello,

Before asking for help on this, let me say I am truly impressed by the 9.04 release thus far. I was simply amazed when everything 'worked' out of the box. Thanks for the great work.

I recently setup version 64 bit 9.04 on my machine. I have a NIC that stays unplugged, and a DWA-140 Wireless-N adapter that works great when logged in; however, it seems that this immediately disconnects upon logout. I've seen a few similar issues on Google, but couldn't find a resolution.

I have setup FreeNX and verified it was working last night via the LAN, after which I logged out and went to bed. Now that I am at work I am unable to connect. I SSH'd into an Ubuntu server at home and attempted to ping the machine, but no reply. Can anyone verify if this is the case, and if so does anyone have a workaround? This was my first assumption, as I noticed it renewing my connection upon the several login/logoffs I had upon initial setup.

Thanks!

---

### Post by jeremyswalker on 2009-10-12
Try to right click on the Network Manager applet in the system tray and click "Edit Connections". Once open, click on the "Wireless" tab. Select your network and click "Edit". Once open click "Available to All Users" at the bottom and click "Apply". Enter your password, and you should be all set.

I use to do this on my desktop when I used a wireless connection. This way, even with no one logged in I could access it remotely.

---

### Post by ff8jake on 2009-10-12
> **jeremyswalker said:**
> Try to right click on the Network Manager applet in the system tray and click "Edit Connections". Once open, click on the "Wireless" tab. Select your network and click "Edit". Once open click "Available to All Users" at the bottom and click "Apply". Enter your password, and you should be all set.

I use to do this on my desktop when I used a wireless connection. This way, even with no one logged in I could access it remotely.Awesome, I'll give that a shot as soon as I get home and post the results. It's a great feature (I can see where it could have it's uses) - but it caught me off guard. :)

---

### Post by ff8jake on 2009-10-12
Thanks Jeremy, worked perfect. Currently connected via nx from work. :popcorn:

Cheers

---

### Post by Iowan on 2009-10-12
I sure hope I can remember this one when the time comes... =D>
(subscription added)
If the problem is [SOLVED], there's an   **Thread Tools** option to mark it as such.

---

