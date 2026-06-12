---
title: "Rubyripper - Configure external USB CD-DVD Drive"
date: 2009-11-22
forum: Multimedia Software
---

### Post by nomnex on 2009-11-22
Hi,

The defaut CD-DVD of my notebook is dully recognized in the Cdrom device as

```
/dev/cdrom
```But I am using an external CD-DVD Drive (USB) and Rubyripper does not recognize it. What's the correct configuration to make the drive work?

The only workaround I have found so far is (since my CD-DVD was referenced by rubyripper as /dev/sr0):


**Question 2:**
Is there a way to speed up the RIP (when quality does not matter - no track check) I could do that with EAC.

---

### Post by michael.conner on 2009-12-01
I just got my external CD drive working with it. It's /dev/sr1 (my internal drive is /dev/sr0) -- I discovered it by trying to play a CD in VLC and seeing how it referenced the drive.

---

### Post by nomnex on 2009-12-02
I forgot to close this thread.

[http://ubuntuforums.org/showthread.php?t=799621&page=2](http://ubuntuforums.org/showthread.php?t=799621&page=2)

see: post #89

Question 2: answer is NO - the developer refuses to let users having a fast rip option (i.e. no check, or "0" vs. "min. 2") to keep a quality standard

@michael.conner
thanks for the input.

---

