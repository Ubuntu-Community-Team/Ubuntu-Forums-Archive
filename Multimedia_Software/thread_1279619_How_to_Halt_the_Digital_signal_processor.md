---
title: "How to Halt the Digital signal processor"
date: 2009-10-01
forum: Multimedia Software
---

### Post by niiize on 2009-10-01
My Sidplayer is currently using this processor playing a tune. But it's running in the background w/o any gnomebased app, and I dont know how one halts it.

Any idéa..

Thnx!

---

### Post by Littleweseth on 2009-10-01
Kill it by process ID, from the terminal. 2 steps :

1) Find the PID. Do 'top' or 'ps aux | grep sidplayer' to find the numerical process ID, say #NNNN. Here's an example where I find the PID of my irssi process :

```
caradoc samba # ps au | grep irssi
lws      26480  0.0  0.6   7804  3184 pts/3    S+   Aug15  32:24 irssi

```

The PID is the first number, '26480'. (Hey, that's a nice number... all the even numbers in a row. Heh.)


2) Kill that process with 'kill NNNN'; this sends a 'kill signal', a polite notification that you'd like the program to quit. Especially stubborn processes may require the -9 flag, 'kill -9 NNNN', which means "DIE **RIGHT NOW**".

---

### Post by niiize on 2009-10-01
thnx very much. woked! :D

---

