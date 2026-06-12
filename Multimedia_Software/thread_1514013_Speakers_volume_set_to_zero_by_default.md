---
title: "Speakers volume set to zero by default"
date: 2010-06-20
forum: Multimedia Software
---

### Post by Padro89 on 2010-06-20
Hi
I'm using ubuntu lucid lynx (64bit).

In alsamixer, the speakers volume is set to zero and I can't hear anything (headphones work properly, though). I turn it up and the speakers work, but each time I reboot it goes back to zero. I've gone through the alsa wiki without finding anything. Can someone tell me how to change the default values in alsamixer so speakers work on start?

Thanks.

---

### Post by Padro89 on 2010-06-21
I found this command in [this thread]("http://ubuntuforums.org/showthread.php?t=205449")

```
sudo alsactl store 0
``` (where 0 is the sound card number)

which is supoosed to save the alsa configuration even after rebooting but it didn't work.

In case I haven't explained properly, I leave here a screen caption where you can see the default configuration in alsamixer I want to change.

[[IMG]http://img683.imageshack.us/img683/3963/selecci001.th.png[/IMG]](http://img683.imageshack.us/i/selecci001.png/)

Thanks again.

---

### Post by lidex on 2010-06-22
Do this. Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

### Post by Padro89 on 2010-06-22
Thanks! Commenting the line in default.pa was enough! After rebooting the sound still works.

Where can I find information about this configuration files, by the way? I'd like to know more about this subject, as sound is a usual problem for me.

Thanks again!

---

### Post by syed.rakib.al.hasan on 2011-01-27
> **lidex said:**
> Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.


great solution..... thanks. :guitar:

---

### Post by satya10123 on 2012-06-10
> **lidex said:**
> Do this. Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```
Thanks buddy.. Its working fine now !!

---

