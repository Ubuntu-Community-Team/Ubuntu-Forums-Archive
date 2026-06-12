---
title: "SOUND Randomly cuts off"
date: 2010-09-06
forum: Multimedia Software
---

### Post by mas_sergio on 2010-09-06
When I'm listening to music or watching youtube videos the audio will automatically go off at any given (random) time. The only temporary fix (wich is not a solution to the problem) is to close FireFox or the audio application and restart it again but later again it will randomly cut off the sound on all applications AGAIN and doing this over and over gets tiresome.  Sometimes I have to force quit audio applications becuase they become unresponsive at the time this happens. It happens with what ever audio application I use *(Rythim box, Audacious, Totem, VLC, Flash in youtube, Myspace music players, etc)*.

I'm currently running Ubuntu 10.04 LTS + Lattest updates.

I didn't have this problem until I updated.

**What could be cuasing this and does anybody know a quick and easy solution? Thanks!**
):P

---

### Post by pickarooney on 2010-10-31
I can't help but have exactly the same problem.
If you've since found a solution please share. If not, have you considered going back to a good release like Jaunty?

---

### Post by mas_sergio on 2010-11-05
*yes, I did not come back to this thread to post it since I kept forgetting to search my name up and look through all my posts (and who likes to do that? lol). Your reply sent me an email (horaay) and I followed it back here to help you out.*

The fix with me was **TO NOT USE THE REAL TIME KERNEL**. At boot simply select a kernel version wich does not have the "rt" in the tittle and that pretty much ended my problems. I have the ubuntu studio packages installed wich install the real time kernel. Some how, some way, real time kernel is unstable and that is what was responsible for all the audio problems and all the other problems mentioned in this topic.

I hope this solves your problem!:KS

---

### Post by mas_sergio on 2010-11-05
also, for flash, I later found out that using GOOGLE CHROME's browser (which is in the repositories) works BEST for any flash related task. I've pretty much ditched firefox becuase of all the problems with it and flash in ubuntu.

---

