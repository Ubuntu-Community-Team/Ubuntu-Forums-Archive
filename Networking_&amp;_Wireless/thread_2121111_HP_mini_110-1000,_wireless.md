---
title: "HP mini 110-1000, wireless"
date: 2013-02-28
forum: Networking &amp; Wireless
---

### Post by GSPearce on 2013-02-28
hi.  I'm new to Ubuntu and am having trouble with my wireless.  I installed Ubuntu (I think the latest version) on an HP mini and although initially the wireless worked, it is now saying that it is shut off at a hardware switch- I went through the 'software and updates' and found a screen that, listed my wireless and said that it was using a proprietoty driver and is now listing a driver with the title linux in it's name, however it still doesn't work and the toggle to turn the wireless on, on that screen is stuck in the off position.  I found another query in the forums regarding enabling wireless but after running the commands in terminal which solved the other users problem, I find my machine in the same state as before.  WTF?

---

### Post by Hadaka on 2013-02-28
Hi, please open a terminal ctrl/alt/t
copy and paste the following commands
and post their results.

```
lsb_release -a | grep R
arch
rfkill list all | egrep '0|yes'
lspci -n | grep -v 8086 | egrep '0200|0280' |  awk '{print$2,$3}'
lsmod | egrep 'b43|ssb|wl' 
```
thanks

---

### Post by GSPearce on 2013-03-01
okay, I tried entering the code but can't get the vertical line to work- tried changing my keyboard layout to American English and still couldn't get it- how do I make that symbol work (I've never used it before on any keyboard so no clue)?  btw my hp mini is a 110-1000 and I'm running Ubuntu 13.04.  You are apparently more of a seafood lover than I.  Thanks for the quick response.

---

### Post by Hadaka on 2013-03-01
Hi, sorry about that, why i suggested to copy and paste
the commands.  the "  |   " symbol is on the right side
of my american keyboard above the \  back slash key.

if you would care to copy and paste one line at a time
here are the commands again..

```
lsb_release -a | grep R
arch
rfkill list all | egrep '0|yes'
lspci -n | grep -v 8086 | egrep '0200|0280' |  awk '{print$2,$3}'
lsmod | egrep 'b43|ssb|wl'
 
```
thanks.

---

