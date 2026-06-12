---
title: "Why is BitTorrent so SLOW?!"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by Ubuntu Joe on 2007-01-18
Please, someone tell me . . .

So, I'm trying to download some free vidoe via BitTorrent . . . 351 MB shouldn't take 48 hours!!  The download rate is fluctuated between 1.0 KB/s and 5.0 KB/s . . . What gives?!

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by taurus on 2007-01-18
Depends on what you download!  Check your firewall; check your router...

---

### Post by an.echte.trilingue on 2007-01-18
Could be lots of things.  In my case, the ISP throttles BT to 10 kbps, and there is nothing I can do about it.  However, remember that BT is p2P, and you can only download as fast as others can upload, and others might not be uploading at all, or there might be so many leechers with their upload rates set to 0 in your swarm that people who are uploading are split between too many clients.  You can improve the BT environment in general by making sure that your upload settings are good (which ironically usually meanings limiting your upload rate to around 54 kbps and limiting the number of upload slots to 4), but you will only see the benefit of this if others choose to do the same (see the "prisoners dilema" on wikipedia).

In general, though, BT is something for your computer to do in the background for weeks at a time, working on many files at once.  

Sorry,
-mat

---

### Post by tagginannie on 2007-01-18
> **taurus said:**
> Depends on what you download!  Check your firewall; check your router...


Some times it not your firewall or router etc. Bit torrent just sucks. I use my friends computer to download large files because she has DSL. I got constant timed out messages, took almost an hour for my download to resume and when it did the rate 
 at best the rate was 2.0. BT just plain sucks


Suzy

---

### Post by an.echte.trilingue on 2007-01-18
> **tagginannie said:**
> Some times it not your firewall or router etc. Bit torrent just sucks. I use my friends computer to download large files because she has DSL. I got constant timed out messages, took almost an hour for my download to resume and when it did the rate 
 at best the rate was 2.0. BT just plain sucks


Suzy

I disagree.  It can really rock.  The problem is not the program, the problem is the swarm environment that each file is in.  When a buddy of mine downloaded FC6, his average down speed was over 200 kbps.  The reason for this is that almost everybody who downloads FC6 continues to seed for a while after their download completes, creating a very healthy swarm that goes really fast.

In the case of things like pirated movies, typically very few people seed (less than 1/3 at any given time), meaning that the seeders are divided among many leeches, and very often these selfish leeches even set their upload rate to zero during the DL, slowing the process very much for others.  While the individual who is leeching is not likely to notice this, it destroys the swarm's environment.  

This is a perfect example of the [prisoners dilema]("http://en.wikipedia.org/wiki/Prisoner's_dilemma") (this page is long but worth a read).

Even in the cases where BT is slow, though, it can still be a very useful tool, but it becomes  a case of using the right tool for the right job.  If you have an always on internet connection and a computer that you leave on all the time, you can download many things at a time at a slow rate that you would not be able to get from a direct download.  If you don't have these things, though, it is probably better to by a hard copy of the file you are looking for or to try to find somebody generous enough to set up an IRC server that will shoot it to you at around 50kbps.

Anyway, have a good one.

Take care
-mat

---

### Post by Ubuntu Joe on 2007-01-18
Well, that makes me feel better . . . I thought it was just me . . .

Where can I adjust Upload settings?

(I'm new at this if you couldn't tell.)

---

### Post by fearevilleet on 2007-01-18
Switch to news groups, its what I did

---

### Post by zanglang on 2007-01-18
That depends, what program do you use? It should be in Options, somewhere along Networking / Bittorrent / Transfer / General in most programs.

---

### Post by Ubuntu Joe on 2007-01-18
I'm just using the BT that comes with Gnome . . . I think it's called BitTorrent, right?  Are there better ones?

Where are the healthiest swarms?  I'll happily seed them!  (So dirty!)

;)

---

### Post by Mis_Uszatek on 2007-01-19
I had 5.10, now I have 6.06. In both cases I had a similar problem.
Bittorrent out of box was very very slow(I have made a comparison with torrent on Windows, on Ubuntu 20kb was the best what I have got, in Windows it was usually 150-300kb).
UbuntuForum->search->...
In my case it was an IPV6 problem. Check do you have this module, if yes, try to wipeout it. When I have done it, bittorrent have started to be 5-10 times faster, but it is in my case.
But you could try.

All info you will find here

[http://ubuntuforums.org/showthread.php?t=126221](http://ubuntuforums.org/showthread.php?t=126221)

---

### Post by zanglang on 2007-01-20
That would be the Upload tab, next to Download. It's pretty popular to use uTorrent on Wine, Azureus and the Mainline client on linux.

And you could always help seed some Linux isos. ;)

---

### Post by phrozen076 on 2007-02-01
hey
im completely new to unbuntu, but im getting absolutely sick of corporations controlling everything...ie, my ipod just died and no customer support, cause im out of the warranty time (by days)....i was wondering if someone knew of a program like utorrent that worked on linux....utorrent is the best torrent program ive ever used, and dont want to lose it.

---

### Post by zanglang on 2007-02-01
You can actually run uTorrent on Ubuntu, using wine (type 'aptitude show wine' for details). It works pretty darn good. ;)

---

