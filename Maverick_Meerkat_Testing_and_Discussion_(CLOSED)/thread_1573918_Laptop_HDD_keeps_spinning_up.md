---
title: "Laptop HDD keeps spinning up"
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by paradoxni on 2010-09-13
Since I wiped 10.04 (64bit) and installed 10.10 (64bit), my samsung sata HDD (HM250HI) keeps spinning up. Any time I do anything that needs disc access, which is just about everything, I keep hearing a slight whirring sound as the disc spins up. 

This did not occur in 10.04.

Laptop is a Dell 1525 and the drive is only a few months old.

SMART Load Cycle Count appears to be nearly 3million! which seems crazy and is increasing by 1 every second!

Any ideas what's causing this or commands I can run to provide further information?

thanks,

---

### Post by cariboo on 2010-09-13
If you install and run powertop, it may give you a clue as to why the drive is spinning up. I've got a samsung HM160HI in my Compaq netbook, my load cycle count is at 23361 and hasn't changed in the last 10 minutes.

---

### Post by recluce on 2010-09-13
On a side note to the OP: you need to fix this ASAP, the number of load cycles within the useful life of a drive is limited. My 2.5 years old drive sits at 93000 cycles, the SMART attribute connected reads 055 - which means that 45% of the design cycles are used up.

If you are really at 3,000,000 cycles, you need to check the normalized SMART value. If that parameter is at zero or close to it, you cannot trust that drive any longer.

---

### Post by psusi on 2010-09-13
You said why it spins up: you did something that needs access to the disk.  The real question is why does it keep spinning down so fast?  Did you install any power management packages like laptop-mode?

Most laptop drives are rated for 300,000 to 500,000 load cycles, so I'd say your drive is hosed if it's already over 3 million.

---

### Post by paradoxni on 2010-09-19
ive tried laptop-mode and setting hdparm -B to 254 and 255, however the drive still spins down after about 20secs idle, and then spins up again when i try to use the laptop.

---

### Post by ljrmorgan on 2010-09-20
Have you tried going to System > Preferences > Power Management and un-checking "Spin down hard disks whenever possible"?

I had the same problem on my netbook when it wasn't plugged in to the mains, doing the above seems to have fixed it (from what I can tell anyway).

---

### Post by paradoxni on 2010-09-20
I've unchecked the spin down option on both battery and plugged in - this was actually one of the first things I did when I noticed this issue. It seems to have no effect what so ever, as with disabling power mangegment with hdparm -B 255.

This did not occur in 10.04.

---

### Post by skeve on 2010-09-21
my laptop behaves the same way when it's working on battery; it didn't happen about a month ago, though I was already testing 10.10 at the time.
So I guess some of the latest updates created this problem.

I checked the power management configuration and disabled this "Spin down hard disks whenever possible" option, but that didn't help either.

---

### Post by willyboy666 on 2010-09-22
this problem is killing me,
on battery power ,whenever i do software update the hd spins down(3-4 times) and stops for 10-15 sec(laptop freeze) then it spins up and it continue installing . p.s (it happened too while i am using firefox browsing the net)

the options in power management ARE not respected (i unchecked spins hd down but it still do) 


i am clueless ...

---

