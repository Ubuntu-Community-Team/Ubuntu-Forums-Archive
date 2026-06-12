---
title: "HP dvd1040 lightscribe stopped working in 9.10"
date: 2010-01-18
forum: Multimedia Software
---

### Post by rottenart on 2010-01-18
So, I have an HP dvd1040 lightscribe DVD/CD burner. All through 8.10-9.04 it worked flawlessly. I used DeVeDe to convert tons of stuff and it always burned no problem. Same with my data discs of .jpgs and audio cds. I used Brasero mostly, because there were never any problems.

All that changed with my upgrade to 9.10 Now, the same burner simply will not work with any program. It will read a CD fine and it recognizes blank media, but every time I try to burn something, it fails. I've gone through Brasero, K3B, Gonmebaker, Xfburn. Every one returns an error.

When I attempt to burn, eacj of these programs starts the process and I can hear the drive spinning. It will spin, stop, spin, stop...

I've noticed lots of people having problems with burning and 9.10 but I thought I would ask about specifics with my HP drive. Please help! This is very frustrating!

---

### Post by rottenart on 2010-01-18
Bump?

---

### Post by rottenart on 2010-04-19
Really, no one? Bump? Please help!

---

### Post by rottenart on 2010-04-20
Bump! Aaaargh!

---

### Post by bunnsguy on 2010-07-26
I've got the same problem...this is quite a disappointment

---

### Post by rottenart on 2010-07-26
So, after some fiddling, I think I have the solution. In Bravero, or most any other burning software, it usually sets the write speed as "highest possible" or something like that. With Brasero specifically, I merely set the write speed to a definite number, I believe it was 24. Evidently, when the software asks for a speed, and the drive itself doesn't have a set target, it can cause the drive to just quit. 

Setting the speed manually worked for me!

---

