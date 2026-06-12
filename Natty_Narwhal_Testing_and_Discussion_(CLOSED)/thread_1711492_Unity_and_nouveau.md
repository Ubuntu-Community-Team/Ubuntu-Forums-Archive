---
title: "Unity and nouveau"
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ngsupb on 2011-03-21
Hi,

Unfortunately the proprietary driver doesn't work well for me (serched a lot, tried a lot of different options). For some reason 2d (3d?) performance with compiz on 8400m is very bad on large resolution, it is fine on default notebook's 1240 though, but not on an external display. 
For my surprise the experimental drivers are free from the bug, and work at acceptable performance. 
**But crashes happen more!** So my questions:

1) Do the developers pay attention to bug reports of unity running on nouveau ?

2) If so how I could help to debug it?

The only thing I see when it crashes is "segmentation fault core dumped"

3) Where those core dump are saved? Don't see them. 

Badly need to make it working more stable, otherwise NO to Unity and Ubunty :(

---

### Post by VMC on 2011-03-21
3) Look at "/var/crash"

---

### Post by cariboo on 2011-03-21
Does /var/log/Xorg.0.log, not give you a reason why it crashed? It's usually the last thing that happened before the segfault.

---

### Post by ngsupb on 2011-03-21
> **VMC said:**
> 3) Look at "/var/crash"

Thanks, something is there but appears the latest I ran are missed.

In case I run unity from shell command with 

"unity" do the core dumps should go there too?

---

### Post by VMC on 2011-03-21
> **ngsupb said:**
> Thanks, something is there but appears the latest I ran are missed.

In case I run unity from shell command with 

"unity" do the core dumps should go there too?

The only time I get unity core dumps is when I use a VT. I'll try it now and see where it goes.

---

### Post by ngsupb on 2011-03-21
> **cariboo907 said:**
> Does /var/log/Xorg.0.log, not give you a reason why it crashed? It's usually the last thing that happened before the segfault.


xorg itself doesn't crash. I couldn't find there anything wrong. Just unity disappears and windows' borders and keys stop working. It is like compiz and unity crash.

I run ctrl+alt+f1
and start from the terminal unity manually.

DISPLAY=:0 exec unity --log /home/vetala/unity.log

There are a lot of sturtup errors in the log. But it works for some time. and suddenly it crashes with the last output  "segmentation fault core dumped" 

I have noticed it happens mostly when I do something in nautilus. 

I have attached the log files of the last crashes. The last line in both files should be "segmentation fault core dumped"
that is what I see in the terminal but it doesn't go to the log. 

Any idea where to dig further?

---

### Post by VMC on 2011-03-21
I just tired using a VT, and ```
unity --reset
``` works, but ```
compiz --replace
``` causes a fatal crash and the results are placed in the "/var/crash" folder to be used for debugging.

---

### Post by VMC on 2011-03-21
> **ngsupb said:**
> xorg itself doesn't crash. I couldn't find there anything wrong. Just unity disappears and windows' borders and keys stop working. It is like compiz and unity crash.

I run ctrl+alt+f1
and start from the terminal unity manually.

DISPLAY=:0 exec unity --log /home/vetala/unity.log

There are a lot of sturtup errors in the log. But it works for some time. and suddenly it crashes with the last output  "segmentation fault core dumped" 

I have noticed it happens mostly when I do something in nautilus. 

I have attached the log files of the last crashes. The last line in both files should be "segmentation fault core dumped"
that is what I see in the terminal but it doesn't go to the log. 

Any idea where to dig further?

Try the command from a Terminal instead of a VT.

---

### Post by ngsupb on 2011-03-21
> **VMC said:**
> Try the command from a Terminal instead of a VT.

Doesn't put crash reports there too :(

The only new file appeared there is _usr_lib_unity_unity-panel-service.1000.crash

for some reason the panel crashed, but unity&compiz worked until they crashed too.  

Usually apport appears on different other crashes to report it but not in this case:(

---

