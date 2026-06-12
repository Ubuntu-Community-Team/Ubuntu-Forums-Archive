---
title: "ubuntu 10.04 Microphone problem"
date: 2010-09-13
forum: Multimedia Software
---

### Post by mamous on 2010-09-13
Hello all...

I have a problem with my microphone, When i installed Ubuntu 10.04 i had the same problem (Microphone not working), So i read some posts and i finally found the solution to install this

> sudo apt-get install linux-alsa-driver-modules-$(uname -r)


[COLOR="Red"][SIZE="5"]it worked[/SIZE][/COLOR]

But before 2 days there was updates in Update manager, and one of them was included (Linux-Alsa-.....) i don't know the pack exactly.

after i finish the update it ask me to restart, after i restart it the microphone stopped working again.

I try to install the pack again no luck,
i have this error on Terminal

> E: Couldn't find package linux-alsa-driver-modules-2.6.32-25-generic

[COLOR="Blue"]BTW: the PPA is there i add it[/COLOR]

So please do u know how can i fix this problem

---

