---
title: "Amarok very slow"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by roida on 2008-01-03
Hello,

When i launch amarok, the all application is very slow ... it strange because i did not change anything and it was working fine for a while ...

I'm pretty new on Ubuntu so could you help me?

Cheers

---

### Post by SyL on 2008-01-03
Is amarok burning the CPU?

---

### Post by roida on 2008-01-03
How can i check that?

---

### Post by SyL on 2008-01-03
Open a terminal and use the top command

```
top
```


or use the system monitoring application

---

### Post by SyL on 2008-01-03
I had a similare issue once.
Amarok was keeping updating the collection ... and therefore using a lot of CPU

if this is the case try:

1/ turn off watch folder option
2/ delete ~/.kde/apps/share/amarok/collection.db
3/ turn on the watch folder option

it worked for me!

---

### Post by roida on 2008-01-03
> **SyL said:**
> Open a terminal and use the top command

```
top
```


or use the system monitoring application

Yes amarok is using a lot of CPU.
I didn't know for this TOP command, thanks!

---

### Post by SyL on 2008-01-03
So try to see if amarok is keeping updating the collection. You can see that on the buttom left of the GUI.

---

### Post by roida on 2008-01-03
> **SyL said:**
> I had a similare issue once.
Amarok was keeping updating the collection ... and therefore using a lot of CPU

if this is the case try:

1/ turn off watch folder option
2/ delete ~/.kde/apps/share/amarok/collection.db
3/ turn on the watch folder option

it worked for me!

If i do that am i going to loose all my statistics?

---

### Post by SyL on 2008-01-03
Unfortunalty I think so ... as this is the database data
... but this is the only work around I know

---

### Post by roida on 2008-01-03
> **SyL said:**
> Unfortunalty I think so ... as this is the database data
... but this is the only work around I know

Ok i did it and it work!
Thank you!

---

### Post by SyL on 2008-01-03
You're welcome!

but next time try to find the solution on your own there is already few topics about this issue...

---

