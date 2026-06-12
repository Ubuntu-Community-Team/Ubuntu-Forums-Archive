---
title: "Echoing audio, remote front end"
date: 2009-11-13
forum: Mythbuntu
---

### Post by nunrgguy on 2009-11-13
9.0.4 Issue with echoing audio with myth remote front end.
I usually have extra audio buffers selected.
Two days ago, audio on all channels began to echo???
This only occurs on Myth frontend - streaming myth to xbmc and audio is OK.

I turned off extra buffers and had the usual occasional stuttering.
Then turned extra buffers back on and audio now seems to be OK again?

What's the cause of this?

---

### Post by nunrgguy on 2009-11-15
Bizarre, booted up today and the echo is back. Everything OK via xbmc so must be a front end issue.

---

### Post by SiHa on 2009-11-16
Just a thought - you haven't got more than one instance of Mythfrontend running by accident?

I mention it, because I've been tinkering trying to get irexec back up and running with 9.10, and I have a 'Restart Mythfrontend' script that kills it and restarts after a 1s sleep.

Once, just once, yesterday I restarted the frontend, and had audio echoing. As I was ssh'ed into it, I ran```
ps -A|grep myth
``` and was rewarded with two instances of the frontend.

Probably off-target, but thought I should mention it anyway.

---

### Post by nunrgguy on 2009-11-16
It's something I'll check but if there is, it's nothing I've done. Recently if I want to shut the f/e down say to browse the net, after pressing escape and choosing to exit myth, it has been going back to myth and I have to do it again...would that be a symptom of 2 front ends running?

---

### Post by SiHa on 2009-11-16
It certainly would be. If you run the above 'ps' command in a terminal window, I suspect you will find you get two mythfrontend hits.

---

### Post by nunrgguy on 2009-11-16
Cheers SiHa, thanks for the help

---

