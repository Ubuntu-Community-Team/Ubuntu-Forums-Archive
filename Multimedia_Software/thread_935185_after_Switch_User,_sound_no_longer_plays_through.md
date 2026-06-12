---
title: "after Switch User, sound no longer plays through"
date: 2008-10-01
forum: Multimedia Software
---

### Post by bopomofo on 2008-10-01
I'm posting this out of ignorance and desperation...


I recall that before when I would Switch User, the sound (from, e.g., last.fm) would still playthrough even after I logged in as a new user (I could never explain this behavior but I found it useful when playing music but letting an occasional friend log in to her account).


Now I find that when I Switch User, the sound is always killed.


Is there anyway to make the system function one way or another?


I'm on Hardy 8.04 with the latest system updates, but this it seems like it should be a much more general questions. Dare I mention "pulse audio" in this post?

---

### Post by markbuntu on 2008-10-01
Changing users should pretty much stop everything that is running unless it is running systemwide. Pulseaudio is generally started as a systemwide daemon but the applications using it are generally limited to individual users. Ahhh, a clue. 

It could be just a bug that was fixed but then again you could configure the application to run systemwide which, by default, it should not.

Well don't hold your breath this could take a while to figure out. Which application were you using for this?

---

### Post by bopomofo on 2008-10-02
Wow, thanks for the quick reply.

I was using last.fm. I don't imagine that the procsesses from one user are "pretty much stopped," but rather that in this case they are losing access to the sound card, or more likely are being silenced at the Pulse Audio layer. But on this question I am no expert.

I tend to agree that it must have been a "bug" that was then "fixed," but to me it appeared as "functionality" that was "lost." ;-P

Can last.fm run systemwide? I'm not sure how to do this, but I would like to figure out how to let certain audio applications play through even if I switch users.

---

### Post by eye208 on 2008-10-02
[https://bugs.launchpad.net/ubuntu/+bug/213149](https://bugs.launchpad.net/ubuntu/+bug/213149)

---

### Post by krul on 2008-10-07
Anyone found a workaround for this????

I really don't like this new 'feature' :sad:

---

### Post by JohnJackson on 2008-10-11
> **eye208 said:**
> [https://bugs.launchpad.net/ubuntu/+bug/213149](https://bugs.launchpad.net/ubuntu/+bug/213149)

Thanks, the solution in the link seemed to do the trick for me

Edit: well, it worked once :|

---

