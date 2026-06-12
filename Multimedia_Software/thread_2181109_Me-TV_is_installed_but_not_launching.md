---
title: "Me-TV is installed but not launching"
date: 2013-10-16
forum: Multimedia Software
---

### Post by Bucky Ball on 2013-10-16
Hi,

My problem is exactly the same as this one, which was asked a year and a half ago and not replied to:

[http://ubuntuforums.org/showthread.php?t=2008434](http://ubuntuforums.org/showthread.php?t=2008434)

1/ Launch Me-TV from apps list and nothing happens. No GUI, no sign of life. Look in Synaptic and I have it installed.
2/ Launch from a terminal and get 'me-tv currently not installed ... etc.' I 'sudo apt-get install me-tv' and get the reply 'latest version installed' !!!

Anyone got any ideas? Not sure that Me-TV is being well-maintained right now but thought there was a stable version around. This is weird. Wondering if it's something to do with being specifically for Gnome (I am running Xubuntu but have VLC, xine, etc. installed and a few Gnome dependencies). 

Had it working fine during the last Olympics. Haven't used it again until about six months ago and didn't work at all for some reason. Kernel updates the cause? Had no luck since but trying to get to the bottom of it.

I am running 12.04.3 with kernel = 3.2.0-54-generic. Me-TV version 1.4.0.

* Further info: Thought I'd try this:

```
sproinks@tosh:~$ me-tv-client
Me TV 1.4.0.12
2013-10-17 00:03:56: Me TV Server 1.4.0.12 started
2013-10-17 00:03:56: An unhandled exception was generated
2013-10-17 00:03:56: Error: The Me TV database version does not match the Me TV server version.
17/10/13 00:04:01: Exception: Failed to communicate with Me TV server
sproinks@tosh:~$ me-tv-server
2013-10-17 00:04:11: Me TV Server 1.4.0.12 started
2013-10-17 00:04:11: An unhandled exception was generated
2013-10-17 00:04:11: Error: The Me TV database version does not match the Me TV server version.
```

Showing the version I have installed, at least. :-k

---

### Post by Bucky Ball on 2013-10-16
Just a thought, I have Me-TV running on another computer, a completely different story which I will post about on another thread sometime (troubleshooting that problem by replicating on my play partition on another machine as the problematic install CAN'T be broken, but I've come across another problem on my test machine ... if you follow!).

Like this: I have 12.04.3, same kernel .54 on both, and Me-TV launches on the other machine but not on this one. Both running straight Xubuntu 12.04.3. Hmm.

---

### Post by sanderj on 2013-10-16
No problems with "me-tv" on Ubuntu 13.04

So ... can you start "me-tv" (not me-tv-client) from the command line?

---

### Post by Bucky Ball on 2013-10-16
Your question is answered in first post of the thread ... in detail. Not interested in 13.04. Thanks.

---

### Post by Bucky Ball on 2013-10-17
The problem is fixed on the other box so thread is not solved or resolved exactly, just no longer relevant as I no longer need to run Me-TV on this computer to troubleshoot it (or for any other reason). Still curious as to the totally odd behaviour, though.

As this same issue cropped up a year and a half ago, I will have a look for a bug report for it.

---

