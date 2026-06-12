---
title: "video downloader for chromium"
date: 2017-11-22
forum: Multimedia Software
---

### Post by acefromspace on 2017-11-22
I have used firefox for years, but having so much trouble with it, I switched to chromium. I am happy with this, but can't download videos. With firefox I used video download helper and it works great. Found something similar for chromium, downloaded it, but it doesn't show up... how do use this? Do I need to log in to chromium? I have a gmail login... it this what I use? I must be missing something... how do I add this to chromium?

---

### Post by Yellow Pasque on 2017-11-23
> Found something similar for chromium, downloaded it, but it doesn't show up... how do use this?
Give a link. We don't know what "this" is.

---

### Post by vasa1 on 2017-11-23
And please keep the [forum's policy on YouTube]("https://ubuntuforums.org/showthread.php?t=1850955") in mind.

---

### Post by acefromspace on 2017-11-23
It's listed as an extension... here's the link

[https://chrome.google.com/webstore/detail/video-downloader-professi/elicpjhcidhpjomhibiffojpinpmmpil?utm_source=chrome-ntp-icon](https://chrome.google.com/webstore/detail/video-downloader-professi/elicpjhcidhpjomhibiffojpinpmmpil?utm_source=chrome-ntp-icon)

Is this a file I need to compile? Can I use archive manager for this? Any other suggestions for a video downloader for chromium?

By the way, I miss firefox. but it is completely unusable... cripples my entire system. Updates don't help. I am using ubuntu 14.10, but soon doing fresh install of 16.04 Maybe then firefox will work.

---

### Post by Yellow Pasque on 2017-11-25
> I am using ubuntu 14.10

What version of chromium are you using? If it's the one that came with Ubuntu 14.10, that may be your issue.

---

### Post by acefromspace on 2017-11-26
Chromium version Version 61.0.3163.79 (Official Build) Built on Ubuntu , running on Ubuntu 14.04 (32-bit)

Another thread mentioned older versions may not support some add-ons (plug-ins, extensions... whatever)
I'm a bit out of practice with terminal (but still love it) How do I compile from source code? Does ubuntu have an easier way?
It's been so long since I've done this... getting older and forget things.

How do I remove and re-install firefox? Was doing fine until it messed up. I will do fresh install of ubuntu 16.04 soon so hopefully firefox will work.

---

### Post by Yellow Pasque on 2017-11-26
What are you trying to compile? You are talking about a Chrome add-on. You click 'Add to Chrome' on its page.

> How do I remove and re-install firefox?

Before doing that, I would try to start firefox in safe mode, especially if you were trying to install extensions the last time it was working:
```
firefox -safe-mode
```

If safe mode works, try creating and running a new profile.
```
firefox -p
```

Finally, you can resort to purging and reinstalling:
```
sudo apt-get purge firefox
sudo apt-get install firefox
```

---

### Post by acefromspace on 2017-11-26
Yes, I did standard add-on through chrome web store. It seemed to download, but nothings shows up to use it (should be a green arrow to the right of address bar)
Thanks for the tips on firefox... knew this but forgot to try a new profile. I will try this first, but going to purge/install anyway (no need to use "remove"?)
This is a good time for me to get back to using terminal.. got lazy.

---

### Post by acefromspace on 2018-01-23
I did get the extension to work, but it does not allow download from you tube (I know... I was warned about this) Consider this solved.

---

