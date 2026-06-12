---
title: "myth-frontend remote load delay 10mins?"
date: 2010-01-04
forum: Mythbuntu
---

### Post by bgiannes on 2010-01-04
I have a problem where the remote will not work in myth-frontend for about ~10 minutes when it's started (not sure of the timing).  Then it just starts working?  Even if i close the frontend and then reopen it, samething?


Note: The IR remote (lirc) works with other programs including myth-backend setup. It has been doing this for about 3weeks now.  As far as i can tell lirc and the remote are not the problem, it must be myth-frontend

---

### Post by bgiannes on 2010-01-06
Bump, Help Please.


Note: The frontend log don't show anything no error....

---

### Post by SiHa on 2010-01-07
Perhaps if you run the frontend from a terminal in verbose mode it might give you a clue.
```
mythfrontend --verbose all
```

This might produce too much info, not sure if there's a specific LIRC argument for the --verbose switch, you can list available options:```
mythfrontend --verbose help
```

---

### Post by bgiannes on 2010-01-10
okay, ive ran the command and loged it.  Its a 3Mb log with alot of info.  ive started looking at it, but im not sure what im looking for.   errors or what.

---

### Post by bgiannes on 2010-01-11
I can't find anything wrong in the log...


After thinking about the problem it seems that mythtv cant use the remote when it 1st starts, but it's only after myth internal player is used that the remote kicks in (after 2+ minutes)?

---

### Post by Neon Dusk on 2010-01-11
Do you use a nvidia graphics card?

There's a long thread on the [mythtv users list](http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=347546;page=1;sb=post_latest_reply;so=ASC;mh=25;list=mythtv) - one of the solutions was adding Option "UseEvents" "True" to the xorg.conf file.

(although this might be different to your problem)

---

### Post by bgiannes on 2010-01-11
> **Neon Dusk said:**
> Do you use a nvidia graphics card?

There's a long thread on the [mythtv users list](http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=347546;page=1;sb=post_latest_reply;so=ASC;mh=25;list=mythtv) - one of the solutions was adding Option "UseEvents" "True" to the xorg.conf file.

(although this might be different to your problem)


I read the thread, i think its a different problem, but thanks for replying.  They talk of the remote becoming inactive during playback from time to time.  I only have no remote at frontend start.  One thing that i did notice is that i also have a HDHomeRun. 

ps I do have a nvidia card

thanx

---

### Post by bgiannes on 2010-01-18
UPDATE:  I had mythbackend crash, when i was messing withit.  after a reboot, the remote now works without having to use mythvideo?

i don't understand why, and i'll need to do some more reboots to confirm the "fix"?

---

### Post by bgiannes on 2010-01-26
okay, the problem is back again.



It seems that after playing Quakelive, the problem came back?

---

### Post by bgiannes on 2010-03-15
just saw this ticket....

[http://svn.mythtv.org/trac/ticket/7921](http://svn.mythtv.org/trac/ticket/7921)

---

