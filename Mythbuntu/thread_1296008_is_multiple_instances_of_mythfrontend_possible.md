---
title: "is multiple instances of mythfrontend possible?"
date: 2009-10-20
forum: Mythbuntu
---

### Post by AJ1000 on 2009-10-20
I have a nova t 500 and have it working successfully in mythbuntu 9.10 beta. One feature I have lost is the ability to run multiple instances of mythfrontend. Which I used to watch two channels simultaneously and it worked. I have noticed that this was considered a bug.

Is there anyway of running multiple instances of mythfrontend simultaneously?

If not, I have a backup of using kaffeine and meTV to produce the same effect.

---

### Post by SiHa on 2009-10-20
> **AJ1000 said:**
> I have a nova t 500 and have it working successfully in mythbuntu 9.10 beta. One feature I have lost is the ability to run multiple instances of mythfrontend. Which I used to watch two channels simultaneously and it worked. I have noticed that this was considered a bug.

Is there anyway of running multiple instances of mythfrontend simultaneously?

If not, I have a backup of using kaffeine and meTV to produce the same effect.

Not sure, but couldn't you use the PiP functionality?

---

### Post by AJ1000 on 2009-10-20
I was just wondering if there was a command line option in mythfrontend to allow multiple instances.

I could not get PIP to work. Do you know how to do this?

---

### Post by SiHa on 2009-10-21
Sorry, I've not tried it myself, I'm just aware that it is (supposedly) possible.

---

### Post by superm1 on 2009-10-21
> **AJ1000 said:**
> I have a nova t 500 and have it working successfully in mythbuntu 9.10 beta. One feature I have lost is the ability to run multiple instances of mythfrontend. Which I used to watch two channels simultaneously and it worked. I have noticed that this was considered a bug.

Is there anyway of running multiple instances of mythfrontend simultaneously?

If not, I have a backup of using kaffeine and meTV to produce the same effect.
It  was intentionally partially disabled because for most people that causes weird behavior (like both instances responding to the same remote).

You can modify the frontend wrapper script, /usr/share/mythtv/mythfrontend.sh to re-enable the functionality.

---

### Post by AJ1000 on 2009-10-21
Thanks, I have decided to use kaffeine and meTV for each adapter instead. 

A flaw I had with two mythfrontends was that I heard sound from both of the two mythfrontends at the same time. With kaffeine and meTv I can mute the sound of either one and listen just to the other.

---

