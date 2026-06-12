---
title: "session ends when starting livetv"
date: 2011-10-11
forum: Mythbuntu
---

### Post by greg_shipman on 2011-10-11
Hello all, this is my first post.  I'll try to make it brief.  First off Mythbuntu 10.10 installed without problem on an old AMD Athlon64 K8 motherboard.  I'm using a Hauppauge Wintv-Nova-T 500 MCE DVB card which is happily detected and drivers loaded.  I'm in Australia so the channel scan found all the free-to-air digital tv channels and the program guide.  I'm using the frontend and backend on the same box.  All seems well until I select 'Watch TV' in the front end.  I see a black screen with the word "Please..." centered followed a few seconds later by the electronic program guide for two seconds and then I'm kicked out of my session and am faced with a log in prompt.  My only clue is from /var/log/mythtv/mythtvfrontend which has an entry:
ICE default IO error handler doing an exit(), pid = 4121, errno = 11
<unknown>: Fatal IO error 104 (Connection reset by peer) on X server :0.0
and then the frontend continues on its merry way.  I've got a Radeon 9200 SE graphics card.  So something in Mythbuntu doesn't like my X configuration.  If anyone had any ideas I'd much appreciate it.

---

### Post by greg_shipman on 2011-10-17
The following is an excerpt from the .xsession-errors file in my home directory:

** (nm-applet:1692): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed
** Message: <info>  disconnected by the session bus.


(xfce4-panel:1429): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:1429): libxfcegui4-WARNING **: Disconnected from session manager.

(xfdesktop:1434): libxfcegui4-WARNING **: ICE I/O Error

(xfdesktop:1434): libxfcegui4-WARNING **: Disconnected from session manager.
xfce4-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfdesktop: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

After googling for the 'ICE I/O Error' I found a number of other occurrences with other applications.  The common denominator is xfce4-session.  In short, it appears Mythbuntu 10.10 seems to be broken.  I've now installed 11.04 and all is working well.  I hope this helps someone else.

---

### Post by thatguruguy on 2011-10-17
Are you able to record shows?

---

### Post by greg_shipman on 2011-10-20
Yes, recording and playback is all good.  Now I've just got to find out how to edit or delete schedules.

---

