---
title: "PS3 Media Server does not start, Java conflict?"
date: 2010-04-04
forum: Multimedia Software
---

### Post by sotvomike on 2010-04-04
I have been using this program for about 2 months now, but all of a sudden yesterday, it doesn't not show up on PS3. I check on my computer and it is frozen. I close it and try to restart. From then on, it never comes back. It seems like it wants to (the tray icon wants to appear but quickly disappears). I check on System Monitor and Java is running (when you hover over it it lists the program) but in the Waiting Channel it is the only program that says futex_wait_queue_me. It is also the 2nd highest memory user (49 MiB). I have done a lot of different things. Tried getting the latest beta release (which did make it pop up but would never start), I installed the new debian package (when it installed it said pms was already running), uninstalling and reinstalling JDK 6. Nothing works. I don't know what in the world would cause it to do this. It was like fine one minute, dead the next. I've tried other servers (Mediatomb won't let me access some of my drives and PS3 doesn't see it, I MythTV's front and backend stuff is way confusing). I love this program and want to continue using it. Help anyone?

BTW, I checked for /tmp/javaps3media/debug.log file and there isn't one.

---

### Post by Flybynight on 2010-04-10
I've just started having the same problem. How I get pms to display in xmb is by restarting pms using the following line in Terminal

```
sudo /etc/init.d/pms-linux restart
```

As soon as it restarts, it appears in xmb.

---

