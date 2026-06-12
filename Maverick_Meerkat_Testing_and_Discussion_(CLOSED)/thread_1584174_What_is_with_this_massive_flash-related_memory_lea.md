---
title: "What is with this massive flash-related memory leak?"
date: 2010-09-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jim March on 2010-09-28
If I have a couple of flash pages going in Firefox 3.6.10 (32bit system, all Meercat updates, ATI open-source drivers on an X1700 video card) and then close the flash pages, memory isn't freed up.  I mean a LOT of memory, 400megs plus in some cases.  If I manually kill "plugin-container" in System Monitor I'll get a lot of memory back, but restarting Firefox without running any flash stuff helps even more.

Is there any way to keep memory usage with flash under a bit more control!?

I "only" have 2gigs RAM on a pretty decent system (Core2Duo T7400, aforementioned ATI X1700, etc.).  Never seen a memory leak this bad in Ubuntu ever.  Should I try the Firefox 4 beta?  Hell, upgrade it all to 64bit and try the new beta 64bit flash?  This is just sad...

---

### Post by Yumi on 2010-09-29
Thanks for this threat. I confirm same problem here and killing plugin-container speeds up operations but only for a short time.

---

### Post by zika on 2010-09-29
> **Yumi said:**
> Thanks for this threat. I confirm same problem here and killing plugin-container speeds up operations but only for a short time.You are using JJ and have this memory leak?

---

### Post by Lucradia on 2010-09-29
> **zika said:**
> You are using JJ and have this memory leak?

uhm, what? This is a meerkat forum, not a Jaunty forum. if you don't want misconceptions, explain everything instead of assuming people know.

---

### Post by Yumi on 2010-09-29
Sorry, I have to update my profile. Am on Maverick latest update. :oops:

---

### Post by zika on 2010-09-29
> **yumi said:**
> sorry, i have to update my profile. Am on maverick latest update. :oops:
:)

---

### Post by zika on 2010-09-29
> **lucradia said:**
> uhm, what? This is a meerkat forum, not a jaunty forum. If you don't want misconceptions, explain everything instead of assuming people know.
:)

---

### Post by Lucradia on 2010-09-29
> **zika said:**
> :)

I usually never look at the miniprofile to the right, err, left. (Silly phpBB)

---

### Post by zika on 2010-09-29
After several errors concerning version the OP uses, I've made myself to notice that info. But, it is not updated always... :)
"Ubuntu Development Release" is, now, a good thing. It doesn't need updating... At least for us, testing junkies... :)

---

### Post by cariboo on 2010-09-29
I have to agree, you still see some people stating that they are using Fiesty, so you give a solution specifically for that version, then the op comes back saying it didn't work, then you try several other things, only to find out quite a bit later that they are using a much newer version, where that specific fix doesn't work.

---

### Post by Jim March on 2010-09-30
Bumping in the hope that it will veer back on topic?

---

### Post by PRC09 on 2010-09-30
Couple of links to read.....Its happening in Windows as well....


[http://support.mozilla.com/en-US/questions/713600?#threadId719044](http://support.mozilla.com/en-US/questions/713600?#threadId719044)


[https://support.mozilla.com/en-US/kb/The+Adobe+Flash+plugin+has+crashed#Disable_hang_protection](https://support.mozilla.com/en-US/kb/The+Adobe+Flash+plugin+has+crashed#Disable_hang_protection)

---

### Post by Jim March on 2010-09-30
OK...is anybody testing the newest flash64 beta?  Are you seeing the same stuff there?

I've tried upgrading to FF4 beta.  I'd say the problem is lessened, as in "plugin-container" is less of a massive hog once flash stops running, but...still obviously an issue.

---

### Post by philinux on 2010-09-30
> **Jim March said:**
> OK...is anybody testing the newest flash64 beta?  Are you seeing the same stuff there?

I've tried upgrading to FF4 beta.  I'd say the problem is lessened, as in "plugin-container" is less of a massive hog once flash stops running, but...still obviously an issue.

Yep. update to the 27/Sep/10 version. No memory leak and normal cpu.

---

### Post by zika on 2010-09-30
> **philinux said:**
> Yep. update to the 27/Sep/10 version. No memory leak and normal cpu.Ditto.

---

### Post by Colonel Kilkenny on 2010-09-30
Keep in mind that browsers keep stuff in memory on purpose.
If you open a tab and close it after it's loaded it might still be in your memory and that doesn't mean that there's a memory leak. It's called caching ;)

I'm not saying that in this case there would be no memory leak (although I kinda suspect there isn't) or a problem. All I'm saying is that good browsers don't free all memory at the same moment you think they should. Some browsers are more aggressive than others but all of them still keep "extra" stuff in memory.

---

### Post by mc4man on 2010-09-30
Maybe it's something with ati - on nvidia both w/ the maverick repo firefox and firefox4 b6 see no indication of a memory leak, nor is memory use very high anyway.
logging the individual pid's associated w/ the plugin thru pidstat shows nothing out of the ordinary and reacts as expected when closing the player(s), and then firefox itself.
(and again comparing free- m before, during and after shows nothing unexpected

---

### Post by Jim March on 2010-09-30
If I've shut down flash and plugin-container is still eating FOUR HUNDRED MEGABYTES!!!!11! then yeah, sorry, I call that a leak rivaled only by what the Titanic experienced.  Or the New Orleans levies during Katrina.  

Four hundred megs isn't "caching".  Sorry.  That's frackin' insane.  Esp. when I've not only shut down flash, I'm also running a WinXP VM and I'm totally balls-out on RAM, system is stuttering, and it's still holding that 400megs.  That's flat-out not acceptable.

> Yep. update to the 27/Sep/10 version. No memory leak and normal cpu.

Are you referring to an update of Flash64, or an update to Firefox4-beta?

---

### Post by juancarlospaco on 2010-09-30
Flash_ IS _a massive memory leak.
:)

---

### Post by cariboo on 2010-09-30
I'm not seeing any massive memory leaks either, running firefox 3.6.10+youtube shows the container uses about 50Mb, and navigating away to another page, the container closes.

---

### Post by Jim March on 2010-09-30
So what version of flash and Firefox are you using, and are you using 32bit or 64bit?

Why in God's name would you say "all good here!" without mentioning details?  WTF?

---

### Post by cariboo on 2010-09-30
As you can see in my post, it's Firefox 3.6.10 and flash is the 64bit v. 10.2 d161.

---

### Post by mc4man on 2010-09-30
I've got to get to work but here is some quick figures from a p4 w/ only 1 GB memory so the %'s are high, memory 'use' lower than with a more modern setup. (somewhat self explanatory comments
(note one could track add. pid's just for the flash player(s) themselves - somewhat unneeded

```
start (free -m
             total       used       free     shared    buffers     cached
Mem:          1000        492        507          0         98        190
-/+ buffers/cache:        204        796
Swap:         1380          0       1380

start firefox 2 instances

             total       used       free     shared    buffers     cached
Mem:          1000        555        445          0         99        221
-/+ buffers/cache:        234        766

start 2 flash players

             total       used       free     shared    buffers     cached
Mem:          1000        768        232          0        102        341
-/+ buffers/cache:        324        676
Swap:         1380          0       1380

pid - 6 @2 players, 6 @1 player, 5@ non flash page, then close firefox (process closes

$ pidstat  -r -p  1826 4 30
Linux 2.6.35-22-generic (doug-desktop1) 	09/29/2010 	_i686_	(2 CPU)

10:38:10 PM       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
10:38:14 PM      1826     38.75      0.00  280356  70920   6.92  plugin-containe
10:38:18 PM      1826     33.00      0.00  280356  71276   6.95  plugin-containe
10:38:22 PM      1826     30.75      0.00  280356  71780   7.00  plugin-containe
10:38:26 PM      1826     16.00      0.00  280356  72036   7.03  plugin-containe
10:38:30 PM      1826     16.00      0.00  280356  72292   7.05  plugin-containe
10:38:34 PM      1826     16.00      0.00  280356  72548   7.08  plugin-containe
10:38:38 PM      1826     47.50      0.00  277340  58684   5.73  plugin-containe
10:38:42 PM      1826     13.75      0.00  277340  58944   5.75  plugin-containe
10:38:46 PM      1826      7.50      0.00  277340  58944   5.75  plugin-containe
10:38:50 PM      1826      3.50      0.00  277340  58944   5.75  plugin-containe
10:38:54 PM      1826      1.75      0.00  277340  59200   5.78  plugin-containe
10:38:58 PM      1826      2.50      0.00  277340  59200   5.78  plugin-containe
10:39:02 PM      1826     36.25      1.00  145368  26944   2.63  plugin-containe
10:39:06 PM      1826      0.00      0.00  145368  26944   2.63  plugin-containe
10:39:10 PM      1826      0.00      0.00  145368  26944   2.63  plugin-containe
10:39:14 PM      1826      0.00      0.00  145368  26944   2.63  plugin-containe
10:39:18 PM      1826      0.00      0.00  145368  26944   2.63  plugin-containe
doug@doug-desktop1:~$ 
 
             total       used       free     shared    buffers     cached
Mem:          1000        674        326          0        102        293
-/+ buffers/cache:        278        722
Swap:         1380          0       1380
```

---

