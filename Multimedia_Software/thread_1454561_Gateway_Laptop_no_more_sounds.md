---
title: "Gateway Laptop no more sounds"
date: 2010-04-14
forum: Multimedia Software
---

### Post by zilu54 on 2010-04-14
After I put my laptop for a system update, some of it [sounds] works selectively in my browser when I am watching youtube but when I am playing some musics on my desktop, there's no any sounds coming out. Then I noticed that my Output is still in 100% but 0.00db and a Dummy Output.

I already tried some steps I saw in some threads that has the same problem too but it became worse, I no more [completely] sounds anymore. :(

Could you guys please help me? any references to follow step by step or resetting why whole system sound?

Thank you.

---

### Post by zilu54 on 2010-04-14
well, its been an hour and still waiting for any response...

---

### Post by lidex on 2010-04-15
Go here first. Work through the howto:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by zilu54 on 2010-04-15
I already tried this "how to" but nothing happened. Why? some of the file are not existed to my system that's why I cannot follow some of the instructions that you gave.

...:( no hope.

---

### Post by lidex on 2010-04-15
> **zilu54 said:**
> I already tried this "how to" but nothing happened. Why? some of the file are not existed to my system that's why I cannot follow some of the instructions that you gave.

...:( no hope.

Go back to that page and install the alsa-backports.
Next run these in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Now REBOOT. Check levels in alsamixer Still no sound? Run this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
and post results here.

---

