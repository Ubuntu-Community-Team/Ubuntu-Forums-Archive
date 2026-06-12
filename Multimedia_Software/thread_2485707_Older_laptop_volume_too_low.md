---
title: "Older laptop volume too low"
date: 2023-04-06
forum: Multimedia Software
---

### Post by Autodave on 2023-04-06
I have an older Acer laptop that I just installed Xubuntu on for an older friend of mine.  While on Firefox and listening to a YouTube video, with the volume all the way up, it is quite soft.  However, if I go into the audio mixer and raise the volume of Firefox from 100% to its max of 150%, the volume is very good.  Unfortunately, after rebooting the machine I am once again stuck at only 100% on Firefox.  I can easily change this, but the person who owns this machine is not going to be able to do this w/o a TON of problems.  Is there a way to lock that volume to 150%?

---

### Post by #&amp;thj^% on 2023-04-06
Set him up with script that simply reads:
```
pactl set-sink-volume 0 150%
```
This should work on 20.04 and up. works currently on 23.04 Lunar as well just now proven.

---

### Post by Autodave on 2023-04-06
Thank you for the reply.  However, I have never used a script before....never had the need to.  How exactly do I use that?  This is for an 80+ year old female that has absolutely no computer smarts.

---

### Post by #&amp;thj^% on 2023-04-08
> **Autodave said:**
> Thank you for the reply.  However, I have never used a script before....never had the need to.  How exactly do I use that?  This is for an 80+ year old female that has absolutely no computer smarts.

Sorry life is a very fast pace for me ATM, Just create an Alias in ".bashrc":
```
alias vol="pactl set-sink-volume 0 150%"
```
To use that at given time, just use "vol" in the terminal.

---

