---
title: "HOWTO: Fix Laptop Wireless Adapter Randomly Not Working"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Martin Marshalek on 2010-05-28
Well, I have been grappling with this problem for the last few weeks and I finally a found a solution of sorts. I have also found a decent amount of posts in the forums regarding this issue so I figured that it would help others if they knew how to fix this.

Okay, what this problem is is that your wireless card cannot be seen by your laptop and simply cannot be re-enabled by restarting or reinstalling. Somehow, for some reason, shutting down, restarting, and probably hibernation end up causing the card to simply shut off. Lspci, lshw, or whatever other command that I do not know of simply cannot see your card. I don't know if this is Broadcom/HP only but you can always test this for other brands as well.

The solution I found is to run a CPU burning program for about 5-10 minutes. It will sound bad, almost like your computer will fly off your desk any second, but it's supposed to do that. Once you terminate the process restart and viola, your wireless card can now be seen. This isn't permanent and your card may revert after restarting or suspending but this fix will re-enable it every time.

DISCLAIMER: Ubuntu Forums and myself are in no way responsible for any hardware damage from using "cpuburn" on your computer.

My recommended program for this is "cpuburn" which is in the repositories. Just run: ```
sudo apt-get cpuburn
```

Then run:```
sudo burn**
``` (replace the asterisks with the letters that correspond with your processor below)

> burnP5   is optimized for Intel Pentium w&w/o MMX processors
    burnP6   is for Intel PentiumPro, PentiumII&III and Celeron CPUs
    burnK6   is for AMD K6 processors
    burnK7   is for AMD Athlon/Duron processors
    burnMMX  is to test cache/memory interfaces on all CPUs with MMX
    burnBX   is an alternate cache/memory test for Intel CPUs


For dual core and above processors, open a new tab in the terminal for each processor and repeat the command in every tab. When you are done press Ctrl+C in each tab to terminate the process and stop the burning. Then reboot.

I hope this helped!

---

