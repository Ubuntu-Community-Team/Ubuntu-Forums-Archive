---
title: "System sound - no app sound"
date: 2010-04-10
forum: Multimedia Software
---

### Post by Wolfsbane on 2010-04-10
I've been googling for a day and found countless suggestions that almost sounds right, but doesn't really help - including unmuting using alsamixer.
Main problem is that I get system sound when I log in, but no application sound. Amarok, Songbird, flash (youtube), younameit - all silent.

Running Lucid Beta 2 on 64-bit Fujitsu 7935 box.
Anything to keep my sanity?

---

### Post by Wolfsbane on 2010-04-10
So no suggestions then?

---

### Post by Wolfsbane on 2010-04-11
Had another go this morning.
Found a How-to to install a bunch of general media apps. This in itself didn't solve anything, but in it was gAlsaMixer which had a bunch of muted channels. Unmuting them, Amarok still didn't have sound. But - on a long shot, KMPlayer did. And YouTube. And Songbird. (Ofc alsamixer - the cli tool - also had muted channel, but I only tested with Amarok). 

[CENTER]:guitar:
[/CENTER]

So the problem is with Amarok 2 atm. Which is my pet hate, so that's ok.
There is a thread out there that unmuted channels revert to muted state on reboot, I'll see if this is the case on my box. I hate when I don't know what the f... was wrong with the setup though.

[CENTER]:popcorn:
[/CENTER]

---

