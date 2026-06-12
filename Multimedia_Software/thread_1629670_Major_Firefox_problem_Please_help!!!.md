---
title: "Major Firefox problem Please help!!!"
date: 2010-11-24
forum: Multimedia Software
---

### Post by Glitchd on 2010-11-24
Hello, I am using Ubuntu 10.04 32 bit on my laptop. Recently I went to update my system which included a firefox update. Upon completing this update flash no longer works (at least with youtube). The following image is what displays on the screen when I try and play a youtube video in firefox. (image in attachments) Any help would be greatly appreciated. Thanks for all the help!

---

### Post by xc3RnbFO8P on 2010-11-24
Try to start Fireox in Terminal, and play video:

> XLIB_SKIP_ARGB_VISUALS=1 firefox

---

### Post by cpmman on 2010-11-24
Try _***[Flash-aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/")***_ from lovinglinux.

---

### Post by Glitchd on 2010-11-24
ok so i tried both of those,
neither work.
i still get a gray/black box with audio only when i access youtube or hulu.

---

### Post by Glitchd on 2010-11-24
> **Glitchd said:**
> ok so i tried both of those,
neither work.
i still get a gray/black box with audio only when i access youtube or hulu.

i should also add, youtube and others work in chrome.

---

### Post by wojox on 2010-11-24
If you open a new tab and type in 

```
about:plugins
```

Does it see Flash?

Look around here as well [Firefox Tutorials]("http://firefox-tutorials.blogspot.com/")

---

### Post by Glitchd on 2010-11-24
im guess so.
it says this.
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

---

### Post by Penguin=) on 2010-11-24
You might have to degrade your Firefox

---

### Post by Glitchd on 2010-11-24
ok, how would i do that?

---

### Post by Glitchd on 2010-11-24
the only solution i can find to this problem is to downgrade firefox.
sadly.

but here is how i did it.

You can download the the .tar.bz2 from the Mozilla website and use that until the Jssh plugin gets updated:
[http://www.mozilla.com/products/down...nux&lang=en-US](http://www.mozilla.com/products/down...nux&lang=en-US)

then

cd ~/Downloads
cp -R ~/.mozilla ~/.mozillabackup
sudo tar -C /opt -jxvf firefox-3*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.old
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

start up firefox and videos should play just fine.

---

