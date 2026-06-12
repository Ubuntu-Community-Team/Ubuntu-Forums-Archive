---
title: "My Microphone Won't Work!"
date: 2009-01-18
forum: Multimedia Software
---

### Post by DizzyEwok on 2009-01-18
Hi, 
I have been using my in-built mic for quite a while now, all of a sudden, it stopped working. Has anyone got any idea? This is what happens:
```
xav@xav-laptop:~$ lspci | grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
xav@xav-laptop:~$ 
```
I'm not an expert in this field, so readable instructions are necessary!

Thanks in Advance

---

### Post by DizzyEwok on 2009-01-18
Bump

---

### Post by DizzyEwok on 2009-01-19
Bump

---

### Post by gettinoriginal on 2009-01-19
Try going into terminal and type

```
alsamixer
```

Then change the option all the way on the right the is labeled "Digital" but above it says analog. Change that option to say Digital. worked in my case...

---

### Post by Roasted on 2009-01-19
My microphone doesn't work. When I hit "alsamixer" I only get 1 thing that shows up... not multiple.

---

### Post by gettinoriginal on 2009-01-20
Right click your sound icon on panel and select "open volume control", make sure it isn't muted.

---

### Post by Roasted on 2009-01-20
> **gettinoriginal said:**
> Right click your sound icon on panel and select "open volume control", make sure it isn't muted.

Building on this, I had to go to preferences and make sure microphone and microphone capture were checked. Then, a "recording" tab appeared. When I clicked on that tab, the microphone volume level was listed. It was not checked "muted" but it was down to 0%. I raised it and now my microphone works. If only I can figure it out in skype now...

---

### Post by gettinoriginal on 2009-01-20
Since Skype is proprietary, you might check their site for a solution. :D

---

### Post by DizzyEwok on 2009-01-20
Ive fixed it! When I went to alsamixer, I changed Mic to full, and it worked!

Thanks to all of you!

---

