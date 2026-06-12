---
title: "Why does Firefox updates make it freeze"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by Morgonte on 2010-09-21
Since june 2010 has every new update of Firefox caused it to freeze immediately after launching it, no window shows but it's there in the list of sleeping processes. Trying to launch it a second time results in the message "Firefox is already running". 
The workaround is to remove the .Mozilla folder in my home directory, then Firefox works until the next update, but of course I have to reenter all settings and add-ons.
Anybody know why this occurs?
I now run Firefox 3.6.10 with Xmarks and Downthemall add-ons.

---

### Post by zealibib slaughter on 2010-09-21
I'm thinking its something to do with the xmarks add on.  I had a nightmarish time with firefox recently until I done as you did and delete my firefox folder.  I've also noticed that xmarks is a common add on for posts with firefox problems here and at mozillas help forum.

---

### Post by realzippy on 2010-09-21
...try reinstalling *xulrunner*.

```
sudo apt-get --reinstall install firefox-gnome-support firefox libcairo2 xulrunner-1.9.2 xulrunner-1.9.2-dev xulrunner-dev
```


...solved this issue for me.

---

### Post by kostkon on 2010-09-21
In most cases, this is happening when the update manager is restarting your Firefox automatically (assuming that it was running when you applied the updates). Thus, either close Firefox before starting an update that is going to upgrade Firefox related packages or in any case try giving the following command when Firefox freezes:
```
pkill firefox
```

---

### Post by lovinglinux on 2010-09-21
Like pointed before, xmarks could be the culprit. There are also other addons that cause similar issues, like Moonlight (libmoon) and Prism.

Nevertheless, your problem looks more like an issue with *compatibility.ini* or *secmod.db* files. Try my extension [ProfileCleaner]("https://addons.mozilla.org/en-US/firefox/addon/213326/"). Let me now if it works for you.

---

### Post by Morgonte on 2010-09-22
Thanks to you all for good input!
Guess what. This morning Firefox refused to start although I have not updated it. I tried realzippy's suggestion of reinstalling xulrunner (and all the other packages in your code) and that seemes to have solved the issue, at least for now. 
I will wait a few days until I mark this thread solved, but hopefully it is! :)

---

### Post by realzippy on 2010-09-22
Fine.Here it works since a week,no more freezes.Admit the command was a broadside,do not know which package exactly caused the issue,but who cares?

---

### Post by Morgonte on 2010-11-26
Ok, here we go again. Since last update of firefox it freezes during launch. I can get it back by deleting the .mozilla directory, but next time I launch Firefox same again. Not even realzippy's broadside will change this. Firefox will not even run in safe mode...
Since last I've changed xmarks for Firefox sync.

---

### Post by lovinglinux on 2010-11-26
> **Morgonte said:**
> Ok, here we go again. Since last update of firefox it freezes during launch. I can get it back by deleting the .mozilla directory, but next time I launch Firefox same again. Not even realzippy's broadside will change this. Firefox will not even run in safe mode...
Since last I've changed xmarks for Firefox sync.

Try [ProfileCleaner]("https://addons.mozilla.org/en-US/firefox/addon/213326/").

---

### Post by Morgonte on 2010-11-27
> **lovinglinux said:**
> Try [ProfileCleaner]("https://addons.mozilla.org/en-US/firefox/addon/213326/").

Yeah, actually I logged on now to write that ProfileCleaner set to delete secmod.db seemes to solve the issue. Good work! I shall wait until next update of firefox until I mark the thread solved, though.

---

### Post by lovinglinux on 2010-11-27
> **Morgonte said:**
> Yeah, actually I logged on now to write that ProfileCleaner set to delete secmod.db seemes to solve the issue. Good work! I shall wait until next update of firefox until I mark the thread solved, though.

Glad to read that. This problem comes and go with different Firefox versions, so is a good a idea to disable the extension after Firefox updates and test if the problem persists. There is no reason to use it if the problem goes away. However, keep the extension installed, in case a new version introduces the problem again.

---

