---
title: "Youtube won't play"
date: 2009-12-17
forum: Multimedia Software
---

### Post by PDA1 on 2009-12-17
I'm using Firefox 3.5.5.

When I click to play a Youtube video only the "black screen" area appears (yes, all of the comments appear below the video screen) and the video doesn't play.

How do I fix the problem?

---

### Post by HappyFeet on 2009-12-17
Please (always) provide more info. What version of ubuntu? 32 or 64 bit? How did you install the flash plugin?

---

### Post by VastOne on 2009-12-17
> **PDA1 said:**
> I'm using Firefox 3.5.5.

When I click to play a Youtube video only the "black screen" area appears (yes, all of the comments appear below the video screen) and the video doesn't play.

How do I fix the problem?

Have you ever been able to see a video there? Are you getting any flash error messages?

---

### Post by PDA1 on 2009-12-17
> **HappyFeet said:**
> Please (always) provide more info. What version of ubuntu? 32 or 64 bit? How did you install the flash plugin?


9.10


32 bit (I assume it's 32)

Flash plugin?  I have no idea.  I know it's supposedly installed but since it doesn't work properly I assume there's some sort of trouble.

---

### Post by PDA1 on 2009-12-17
> **VastOne said:**
> Have you ever been able to see a video there? Are you getting any flash error messages?


Yes.


Earlier IT (youtube) told me to install some Adobe flash player program.  So, I did.  No change.

---

### Post by VastOne on 2009-12-17
> **PDA1 said:**
> Yes.


Earlier IT (youtube) told me to install some Adobe flash player program.  So, I did.  No change.

How did you install the plugin?  And which one?

---

### Post by PDA1 on 2009-12-17
I clicked on the link in Youtube and it took me to Adobe where I downloaded the tar file.  

I extracted it.  But since I had no idea where to extract it to I created a folder called "flash player" and put it there.

---

### Post by VastOne on 2009-12-17
> **PDA1 said:**
> I clicked on the link in Youtube and it took me to Adobe where I downloaded the tar file.  

I extracted it.  But since I had no idea where to extract it to I created a folder called "flash player" and put it there.

Follow method 1 at this site


[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

---

### Post by HappyFeet on 2009-12-17
Just do:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by PDA1 on 2009-12-17
For whatever reason, God only knows, the problem is fixed.

---

