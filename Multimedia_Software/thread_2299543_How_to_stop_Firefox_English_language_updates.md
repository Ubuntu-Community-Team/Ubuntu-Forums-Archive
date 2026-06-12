---
title: "How to stop Firefox English language updates"
date: 2015-10-19
forum: Multimedia Software
---

### Post by s9032g@comcast.net on 2015-10-19
I have recently switched to the Xubuntu version 14.04 LTS. I loaded Chromium and thought that I got rid of Firefox; however the Software Updater keeps coming up with English language updates for Firefox which I then uncheck.

I found a lot of questions about this problem going back to 2011. I have tried everything that made sense, such as "sudo apt-get --purge autoremove firefox. When I do this the message is that Firefox does not exist so it cannot be removed. Well something does exist. How can I stop this update?

I do use Thunderbird.

---

### Post by vasa1 on 2015-10-19
What do you get by running```
dpkg --get-selections | grep "firefox"
```

And see Sandyd's post (#6) here: [http://ubuntuforums.org/showthread.php?t=2172030&p=12777800#post12777800](http://ubuntuforums.org/showthread.php?t=2172030&p=12777800#post12777800)

... as well as the posts that follow :)

---

### Post by ajgreeny on 2015-10-19
You probably removed the **firefox** package but not **firefox-locale-en**.  Get rid of that second one and you should not see any more updates of anything "firefox".

---

### Post by s9032g@comcast.net on 2015-10-19
ajgreeny

LIS  Just ask the right person, use synaptic, and the problem is solved.

Thanks

---

