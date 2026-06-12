---
title: "Wlan not working with ANY Linux, but works with XP"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by yaris1 on 2011-06-06
I'm in need of some serious help here.

Problem description:

My wlan is not working on my thinkpad T400, it has the Intel 5100 wlan card. In Win XP everything works well so its not broken.
But with ALL Linux variants I have tried the last few days its just won't connect, I can see the networks and all, so its definitely recieving something, its just tries to connect but never makes the connection.

I have tried Ubuntu 10.10, 10.04, Mint 9, Mint 10, Knoppix, Puppy and a few others. just a few days ago I somehow crashed my Mint 9 install so it booted straight to memtest and it did so for an eternity so I figured it was time to try some other Linux variants. but then came the probmlem - can't connect with any of them.

Its really weird since it worked with Mint 9 last week before the crash, it has worked with Mint 10 before, and it has worked with Ubuntu 10.04 before. It does not connect with any of them now, not even from the livecds which have worked very well before.



Whats going on?

Is there some way I can get a list out of the OS of what should be going on so someone can double check if its correct, or any other type of diagnostics I can do?

Could it be the router? It has worked before with all these above OS'es and it obviously works with XP right now.

There is limited things I can do in BIOS but it looks allright.

Some of the livecds I have are old and they have worked before but not anymore.

I have tried connecting to other routers and its the same problem with all of them, just wont connect.

Its like the password is wrong but obviously its not.

ALL help is appreciated.

---

### Post by yaris1 on 2011-06-06
Does anyone know what *could* possibly be causing this?

Its like the computer all the sudden decieded to just not work anymore with linux. I believe it should be next to impossible for this to happen with all these different linux variations.

I have 20 more to test later, we'll se how it goes.

---

### Post by chili555 on 2011-06-06
How about opening a terminal and run and post:```
rfkill list all
dmesg | grep iwl
lsmod | grep -e wmi -e laptop
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

