---
title: "can't play movies or video's in Banshee and Movie Player"
date: 2013-02-23
forum: Multimedia Software
---

### Post by goodbye-windows(tm) on 2013-02-23
Hi All,

I have a unity system, certified linux capable, 64 bit. I upgraded  from 11.10 to 12.04, and now I can't play mp3's and videos. I suspected the issue was lack of the Ubuntu-restricted-extras, so I installed them using synaptic. There were no errors.

I should note that this was NOT a fresh install, it was done via the upgrade option.

But, when the computer was rebooted, it still refused to play videos and mp3's.

When I try to play a video in banshee, it gives me the same error,  it needs Gstreamer element uridecodebin.

I have reinstalled banshee, including all the helper aps and related files shown in the software center.

Any ideas????

TY

Art

---

### Post by JRV on 2013-02-23
Did you install ubuntu-restricted-extras?
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by carl4926 on 2013-02-23
Try deleting the hidden folder

.gstreamer-0.10

---

### Post by goodbye-windows(tm) on 2013-02-23
Hi JRV,

I did install the restricted extras using synaptic. But, after reading you message, I tried it from the terminal mode. It told me the latest version of restricted extras was already installed. 

I tried Carl's suggestion next, although  I renamed the folder rather than deleting it. This fixed the problem.

TY to you both for making suggestions.

Regards,

Art

---

### Post by carl4926 on 2013-02-23
> **goodbye-windows(tm) said:**
> Hi JRV,

I did install the restricted extras using synaptic. But, after reading you message, I tried it from the terminal mode. It told me the latest version of restricted extras was already installed. 

I tried Carl's suggestion next, although  I renamed the folder rather than deleting it. This fixed the problem.

TY to you both for making suggestions.

Regards,

Art

Great news

---

