---
title: "File Copy Stalls during transfer"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by ortuno2k on 2010-01-18
Hello,

I recently built an Ubuntu Server, and installed 9.10 on it. (I'm fairly new to the Linux, Ubuntu world).

Set up Samba, have proper permissions - etc.

The problem I'm having is copying files from my Mac to the Samba share. I'm copying large files (anything over 100 MB) and during the copy progress, the network connectivity drops to 0 KBps (on the Mac), and it resumes after 3-5 seconds, continuing to copy. It'll start to copy really fast, gives me an estimate time of "x" seconds or minutes, but after a few minutes, the copy time goes up substantially.

Someone else was watching a movie which I had on the share, and while I was copying the files, the network completely stalled for the person watching the movie too. The movie "paused" and kind of "timed-out", and it resumed playing after a few seconds.

For the record, the specs on the Ubuntu server are:

AMD XP-2500 CPU, 1.5GB RAM, WD 1TB Green Drive, Intel Gigabit card

The Mac is connected to the server via ethernet (1 Gbps). The person watching the movie is doing so wirelessly (54g, I think). 

I tried copying some large files from a Windows PC to the share, but the problem didn't repeat - BUT - the network connection was only 10/100 mbps - the Windows machine didn't have gigabit support.

I'm wonder if it's Mac OS or the Intel card on the server.

Any tips as to how to get to the bottom of this? Please!

Thanks.

---

### Post by ortuno2k on 2010-01-18
BUMP.
Anybody, please?

---

