---
title: "Intel 845GL &lt;-&gt; hard disk performance!?"
date: 2005-12-28
forum: Multimedia &amp; Video
---

### Post by adityamalik on 2005-12-28
Hi

I have a laptop with an intel chipset, and the 845GL video thingy (detected as such).

The problems I am facing are:
1. the i810 driver doesn't work except in 640x480 unless I specify the monitor HorizSync and VertRefresh settings..
2. When I do specify them, the disk access and general performance becomes reaaaally slow. almost unusable.
3. I can't seem to compile the latest i810 driver, it keeps saying kernel config file not found even  though to the best of my knowledge I have the kernel source, headers and toolchain installed.
4. Hence I'm using the 'vesa' driver right now.. Even then, the performance (program start up time) is quite a bit more than that under windows XP.

I have only 128 megs of ram (don't ask, plan to change that real soon).. Could that be the reason? Also, my swap partition is 2xMemory.. is that too small?

---

### Post by sciurus on 2005-12-28
What does the output of the "free" command say?

---

### Post by adityamalik on 2005-12-28
The 'free' command says:

                     total       used       free     shared    buffers     cached
Mem:        118616     113180       5436          0        836      33132
-/+ buffers/cache:      79212      39404
Swap:       345356      42288     303068

That's just 5 megs free.. How can I increase that?

---

### Post by sciurus on 2005-12-29
[QUOTE=adityamalik]
That's just 5 megs free.. How can I increase that?[/QUOTE]

Do as you said before and get more RAM. This is undoubtedly a cause of your slowness.

---

