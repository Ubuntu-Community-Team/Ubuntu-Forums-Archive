---
title: "Please Compile This Module For Me..."
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-05-07
Hello people..
I am havin some tuff time trying to compile this thing.
I need Linux_source for this..which I don't have.
its a 35 MB file..that'll take ages to download for me.



[B]I am Presently on Breezy Badger(Kernel 2.6x)
I need you guys to Compile the Kernal Module for me
There is the make file that must be edited acc. to your kernel
Please do it..I beg of u guys...[/B]

---

### Post by tseliot on 2006-05-07
It's for kernel 2.4.x

Isn't the support for RTL8139C+ already in Ubuntu's kernel?

---

### Post by hellmet on 2006-05-07
The thing is that I have RTL  8139D
That card sucks big time
After lotsa search,
I came to know that I'd be able to get the card up
and running if I add one particular line into the thingy.
I did that..
I need someone to get it compiled..
I just can't handle all that Linux stuff anymore for today

---

### Post by mips on 2006-05-07
Have you tried booting with- acpi=off ?

---

### Post by hellmet on 2006-05-07
YES.
But it was of no use.
To know more about all the 'hardships' I faced,
simply have a look at the threads I started.
i feel very frustrated, bcoz i don't have the money(pocket money)
to get myself a new card.
And here I am at a dead end.

How I wish someone wud provide me with the 2.6x version of the driver
for my Card!!

---

### Post by hellmet on 2006-05-07
# kernel  /vmlinuz root=/dev/hda2 ro linux noapic pci=irqroute pci=noacpi acpi=off irqpoll

this is my boot.lst file.
I hope I have done it rite.

---

