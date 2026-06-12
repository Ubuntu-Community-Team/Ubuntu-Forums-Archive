---
title: "Myth Frontend not responding"
date: 2009-02-09
forum: Mythbuntu
---

### Post by Vague Craig on 2009-02-09
Hi all,

I'm having a problem every now and then with the frontend not responding to any input. The remote stops doing anything and the keyboard won't change anything either.
The only thing the keyboard can manage is a ctrl alt del, but this doesn't really help as the frontend keeps playing in the background.
I've had a look at the log and can see nothing out of the ordinary, it only happens during Livetv, at least it has only happened during live tv.
Any ideas, anything worth checking?

Cheers.

---

### Post by newlinux on 2009-02-09
Is this a nvidia video card?

[http://ubuntuforums.org/showthread.php?t=885337](http://ubuntuforums.org/showthread.php?t=885337)

Add 

Option "UseEvents" "on" 

to the nvidia device section of your xorg.conf and then restart X

---

### Post by Vague Craig on 2009-02-09
Thanks for the reply, I've made the change you've suggested, guess I'll have to wait and see. 
It's odd that this has only just started happening recently, this has been fine for a month or so before now.

---

### Post by Vague Craig on 2009-02-12
Ok, so that seems to have done the job, I added:
Option "UseEvents" "on" 

but I noticed I already had:
Option "UseEvents" "1" 

Which was mentioned in the other thread as to be the same, which I'm not quite getting, especially as since adding this line the problem seems to have gone away.

---

### Post by Vague Craig on 2009-02-22
Well unfortunately the problem has come back again. It only ever seems to happen while watching live TV, which as that's all my wife does it's causing some problems.
Any ideas what could cause this, x-org doesn't seem to be overactive when this happens, everything seems normal when I run top, and I find nothing different in the logs.

---

