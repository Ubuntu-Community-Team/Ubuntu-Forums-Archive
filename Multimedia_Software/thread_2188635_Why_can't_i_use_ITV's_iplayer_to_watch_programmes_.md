---
title: "Why can't i use ITV's iplayer to watch programmes i have missed?"
date: 2013-11-18
forum: Multimedia Software
---

### Post by ML7rcEx on 2013-11-18
I am running Ubuntu 13.10 and for some reason i am unable to watch any programmes i might have missed while online on either ITV or BBC iplayers. Could someone help me out here please.

---

### Post by speartip on 2013-11-18
I don't think 13.10 has hal installed which is needed to play itv player. It has also been removed from the repos so you need to install it from the  Hal ppa.

[COLOR=#000000]sudo add-apt-repository ppa:mjblenner/ppa-hal

sudo apt-get update

sudo apt-get install hal


[/COLOR]

---

### Post by philinux on 2013-11-18
I only needed flash for bbc iplayer nothing else.

I just check itv help page and that's the same. Flash.

---

### Post by speartip on 2013-11-18
> **philinux said:**
> I only needed flash for bbc iplayer nothing else.

I just check itv help page and that's the same. Flash.
You might be right. I know hal is needed for 4oD & channel 5 also TVCatchup, but i'm using 12.04LTS so I can't check as all works as it should on 12.04.
Also make sure you have no addons in Firefox like adblock that may be causing your problem.

---

### Post by philinux on 2013-11-19
> **speartip said:**
> You might be right. I know hal is needed for 4oD & channel 5 also TVCatchup, but i'm using 12.04LTS so I can't check as all works as it should on 12.04.
Also make sure you have no addons in Firefox like adblock that may be causing your problem.

13.10 is what OP is running.

BBC, itvplayer, 4OD and TVcatchup all use flash as I've just been watching. Hal not needed.

Only exception to the above is BskyB's SkyGo service which uses silverlight. 

The Op needs to install ubuntu-restricted-extras and they are good to go.

---

### Post by speartip on 2013-11-19
> **philinux said:**
> 13.10 is what OP is running.

BBC, itvplayer, 4OD and TVcatchup all use flash as I've just been watching. Hal not needed.

Only exception to the above is BskyB's SkyGo service which uses silverlight. 

The Op needs to install ubuntu-restricted-extras and they are good to go.

Many users have had issues without hal installed, see thread:
[http://ubuntuforums.org/showthread.php?t=2144347&highlight=4od](http://ubuntuforums.org/showthread.php?t=2144347&highlight=4od)
Before I went back to 12.04 I had the same issue & following #9 or #14 resolved the problem. Hal was needed in my case. So it may be worth a try. I do agree though that the ubuntu-restricted-extras package needs to be installed. In fact it should be the 1st thing done on any clean install imo.

---

