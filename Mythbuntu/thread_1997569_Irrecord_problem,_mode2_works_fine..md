---
title: "Irrecord problem, mode2 works fine."
date: 2012-06-05
forum: Mythbuntu
---

### Post by jaguzu on 2012-06-05
Ubuntu 12.04 with lirc 0.9.0.
i want to config my own remote.
when i type, in terminal, "sudo mode2 -d /dev/lirc0" i can clearly see the pulses.
then i type "sudo irrecord -d /dev/lirc0lirc.conf.test10" and i get the info text...
then "press enter to start..."
i push a button and ONE dot apperas, but after that no more dot appears on the screen. i have tested with two other remotes and both working.

Any idea? /thanks

---

### Post by nickrout on 2012-06-05
you need a space in that command, but I assume it is just a typo?

Are you sure the remote is compatible with the receiver?

---

### Post by jaguzu on 2012-06-06
> **nickrout said:**
> you need a space in that command, but I assume it is just a typo?

Are you sure the remote is compatible with the receiver?

thanks for your reply :)

yes i have used a space in that command, sorry.
hehe the remote isn't bought with the receiver at all.
In what sence could it be incompatible? ...i mean what are the specification that needs to be equal?
I thought the receiver of a black box just listening to ir signals, witch it seems to do in mode2. And then just config my old remote. am i wrong?

---

### Post by nickrout on 2012-06-06
what is the receiver?

What is the remote?

---

### Post by jaguzu on 2012-06-06
> **nickrout said:**
> what is the receiver?

What is the remote?

Don't rembemer the receiver name 100% correct, but something like mceusb. the remote is unknow as it is a toy.
The most confusing right now is why mode2 works fine but irrecord doesn't work. Out of ideas. I was thinking if it was something with the frequency from the remote, but i think "if i get signals in mode2 the receiver works fine with the remote and it should work in irrecord".

---

### Post by azmyth on 2012-06-06
You could have gotten a stray signal when you were trying to do irrecord. The sun and lights and other things generate ir signal and if irrecord gets this it could be confused. Mode2 doesn't care as it will just repeat it back whereas irrecord is looking for length delay etc. I know it sounds off but try doing it a night without any tvs etc on in the room.

---

