---
title: "Default sound card and default mixer"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by RMK68 on 2007-02-18
Hi,

I have the following problems with my sound configuration:

- I have two sound cards and till some times ago, I was able to select live the one I am using by default via the menu System/Preferences/Sound, but I cannot anymore, does anyone has an idea why?

- How is it possible to set Kmix as the mixer by default instead of Alsa mixer?

Thanks for your help.

---

### Post by Yfrwlf on 2007-10-21
> **RMK68 said:**
> Hi,

I have the following problems with my sound configuration:

- I have two sound cards and till some times ago, I was able to select live the one I am using by default via the menu System/Preferences/Sound, but I cannot anymore, does anyone has an idea why?

- How is it possible to set Kmix as the mixer by default instead of Alsa mixer?

Thanks for your help.

I don't think any sound cards should vanish.  That may mean the sound card has been disconnected.  If you do 
```
$ sudo asoundconf list
```
You should see both cards listed.

---

