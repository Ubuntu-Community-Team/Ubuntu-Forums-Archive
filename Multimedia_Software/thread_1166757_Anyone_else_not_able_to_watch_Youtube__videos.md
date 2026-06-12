---
title: "Anyone else not able to watch Youtube  videos?"
date: 2009-05-22
forum: Multimedia Software
---

### Post by Tribulation on 2009-05-22
I've never had much of a problem with Youtube videos on Ubuntu before. I've had a couple times where I had no sound but I could always at least watch the videos. I even watched some earlier, but now, I can't. I don't even see the player.

---

### Post by gandaran on 2009-05-22
have you installed flash?

---

### Post by Tribulation on 2009-05-22
Yeah, it's always one of the first things I do. The latest version of Flash is installed.

---

### Post by gandaran on 2009-05-22
> **Tribulation said:**
> Yeah, it's always one of the first things I do. The latest version of Flash is installed.
do you have flashblock addon installed?
post the output of running these two commands in terminal in the same order
```
sudo updatedb
locate libflash

```
and some info about ubuntu version and if 32-bits or 64-bits

---

### Post by Tribulation on 2009-05-22
No flashblock installed. Nothing has changed in the last several hours (and it was several hours ago that I was watching Youtube videos). I'm using Ubuntu 9.04, 64-bit. 

I get nothing when I run the first command, but after running "locate libflash" I got

```
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashlx.so
```

---

### Post by gandaran on 2009-05-22
> **Tribulation said:**
> No flashblock installed. Nothing has changed in the last several hours (and it was several hours ago that I was watching Youtube videos). I'm using Ubuntu 9.04, 64-bit. 

I get nothing when I run the first command, but after running "locate libflash" I got

```
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashlx.so
```
how did you install flash? I see you don't have the flashplugin-nonfree package installed but installed flash manually in /usr/lib/mozilla/plugins, is this flash 64-bits?

---

### Post by Tribulation on 2009-05-22
Yes, that's how I did it. Originally I installed flashplugin-nonfree but due to problems, installed the 64-bit version instead.

---

### Post by gandaran on 2009-05-22
> **Tribulation said:**
> Yes, that's how I did it. Originally I installed flashplugin-nonfree but due to problems, installed the 64-bit version instead.
okay then, but you have to remove the nspluginwrapper too, it's not needed anymore and it may conflict with the 64-bits flash.
and just to ensure you have the right plugin download again the 64-bits  flash [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") and replace the one in /usr/lib/mozilla/plugins with this one.

---

### Post by Tribulation on 2009-05-22
Alright, I'll have to do that tomorrow. Thanks for the help, I'll report back when I've tried this.

---

### Post by Tribulation on 2009-05-22
Well, the problem still persists.

---

### Post by gandaran on 2009-05-22
okay then, if flash is properly installed and still no work then it must be something wrong with the firefox profile, try this, close firefox and rename the /home/user/.mozilla folder to .mozilla.old, now restart firefox, (firefox will create a new profile) go to youtube and see what happens, if it still won't work you can restore you old profile.
hope this helps.

---

### Post by Tribulation on 2009-05-22
That did the trick for Youtube... for some reason this site looks like crap now. It's doesn't have any boarders, and most things are now white, and I can make quick replies... I haven't encountered any other sites that are messed up though. I won't be too hurt if I can't fix this problem, I can still use the forums at least... Thanks for the help.

---

