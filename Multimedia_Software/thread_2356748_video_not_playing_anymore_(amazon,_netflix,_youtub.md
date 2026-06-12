---
title: "video not playing anymore (amazon, netflix, youtube)"
date: 2017-03-26
forum: Multimedia Software
---

### Post by yoshiki2 on 2017-03-26
Hello. Netflix and Youtube are not playing anymore on (chromium, chrome, firefox). All i remember doing is saying yes when Firefox wanted to install or activate drm to watch netflix. Any ideas?
I'm still new to linux, >.<!!


[RIGHT][/RIGHT]

---

### Post by TheFu on 2017-03-26
I heard that Firefox removed ALSA support last week. They require Pulse audio now.  That will break audio on Ubuntu versions that use ALSA and not pulse. Believe Lubuntu is one of those flavors.

Don't know about youtube or netflix.  Just tested youtube in chromium - seems to be fine.  Don't have netflix streaming and refuse to load the google-chrome-browser, sorry.

I always refuse DRM questions, but don't remember any during the last patch cycle yesterday.

---

### Post by shridhar-kapshikar on 2017-03-29
This might help you, 
[http://askubuntu.com/questions/531672/how-to-install-flash-payer-in-ubuntu-14-04-lts](http://askubuntu.com/questions/531672/how-to-install-flash-payer-in-ubuntu-14-04-lts)

---

### Post by deadflowr on 2017-03-30
> **shridhar-kapshikar said:**
> This might help you, 
[http://askubuntu.com/questions/531672/how-to-install-flash-payer-in-ubuntu-14-04-lts](http://askubuntu.com/questions/531672/how-to-install-flash-payer-in-ubuntu-14-04-lts)

That won't help.

Firefox needs a user agent switcher or it'll try to install silverlight.
As for chrome, maybe try moving or deleting the current user profile and creating a new one.

To move a profile just rename the profile folder located at ~/.config/google-chrome. (Maybe also do the same for chromium at ~/.config/chromium)
simple command would be
```
mv ~/.config/google-chrome ~/.config/google-chrome-old
```
or
```
rm ~/.config/google-chrome
```
to simply remove the profile.

Once the profile is moved or removed the next time you launch chrome, it'll create a new one.

See what happens there.

---

### Post by SeijiSensei on 2017-03-30
Netflix works on my 14.04 system without any fussing if you use Chrome.

I was using Pipelight+Silverlight in Firefox, but since [Pipelight development has ended]("http://pipelight.net/"), that's not really a viable long-term solution any more.

---

