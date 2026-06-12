---
title: "Hauppauge 1600 runs...but audio is full of static"
date: 2009-05-02
forum: Multimedia Software
---

### Post by gohanssjn on 2009-05-02
Anyone else have this issue?  I have no idea where to even begin.

I do remember having to get a patch in Vista because I had this card and 4GB of ram, so maybe it's the same issue...but not patch for Ubuntu?  I am running 32bit, and Vista was 64, so maybe unrelated?

---

### Post by keneo2 on 2009-12-25
Hi, 
did you ever find a solution to your sound problems?
I am having the same issue.
 
Ken

---

### Post by HappyFeet on 2009-12-25
What program are you using to watch tv?

---

### Post by Sum Requiem on 2009-12-25
When my card has no sound running, this is what I do:
sudo rmmod cx18
sudo modprobe cx18

Hope it helps.
Source: [http://ubuntuforums.org/showthread.php?t=1197503&highlight=cx18+sound]("http://ubuntuforums.org/showthread.php?t=1197503&highlight=cx18+sound")

---

### Post by keneo2 on 2009-12-26
> **HappyFeet said:**
> What program are you using to watch tv?
 
I am using Media Portal to record programs from the set top box(stb).  audio comes from the RCA ports on the STB into a 1/8 converter and into the happauge audio input.
 
Perhaps I was hastey to call the problem "static" .  It's more like the sound is easily distorted and it's even difficult at times to understand the words spoken.
 
If I play the file on my computer the sound quality is lower, but its not as bad as other playback devices.
 
I am using XP

---

### Post by HappyFeet on 2009-12-26
> **keneo2 said:**
> 
 
I am using XP

This is an ubuntu/linux support forum. Perhaps you should go to a windows forum for help. Good luck.

---

### Post by gohanssjn on 2010-03-28
Never did get this resolved.  Sigh.

---

