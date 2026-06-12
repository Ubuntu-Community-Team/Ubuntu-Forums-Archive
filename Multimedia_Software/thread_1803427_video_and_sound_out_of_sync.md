---
title: "video and sound out of sync"
date: 2011-07-13
forum: Multimedia Software
---

### Post by HappyLinux on 2011-07-13
In the last week, whenever I play videos, online or offline, the sound and video are out of sync. Usually the sound is a full second behind the videos, but I've noticed it at less.

I just tried watching a video and whenever someone said something, the sound was a full word behind the movement of the mouth.

This never happened until recently. I think there was an update to the sound drivers a couple weeks back, but I'm not too sure.

Can anyone help?

This is becoming unbearable.

---

### Post by handy on 2011-07-13
Its your lucky day:

[http://www.specialops.co.nz/blog/sync-audio-in-vlc/](http://www.specialops.co.nz/blog/sync-audio-in-vlc/)

---

### Post by HappyLinux on 2011-07-13
> **handy said:**
> Its your lucky day:

[http://www.specialops.co.nz/blog/sync-audio-in-vlc/](http://www.specialops.co.nz/blog/sync-audio-in-vlc/)

I've been looking into this matter with limited success. For the offline videos, I can switch from one player or another. VLC has the sync problem on some vids, but SMPlayer and Totem do not. Sometimes VLC isn't out of sync but one of the others is.

However, this doesn't solve the online sync problem like on YouTube for example. I read that deactivating Hardware Acceleration in Flash Player solves the problem, but that setting hasn't worked for me in weeks/months, ticked or not.

---

### Post by handy on 2011-07-16
This won't provide the solution you are looking for either, but it may make the waiting until you find the solution or the next version of Ubuntu comes along more convenient.

Have you tried to use the FlashvideoReplacer Firefox add-on:

[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/#install-beta](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/#install-beta)

It is written & maintained by one of our fellow forum members.

It improved the quality of my Flash experiences on the web.

---

### Post by HappyLinux on 2011-07-16
I know of said forum member. I use his Flash-Aid program, which I had a few problems with until recently. Now I have Flash 11 installed, all the problems seem to have vanished, including the sound sync problem for online videos. I stil have the offline sound sync problem though.

---

### Post by handy on 2011-07-16
So you can't sort out the off-line sync using the tools that VLC provide?

---

### Post by HappyLinux on 2011-07-18
Not at the moment. I have to reinstall VLC because it keeps crashing for some reason. There's nothing wrong with the files that I'm trying to view through it, as the files work in other players. I'll get back to you when I've reinstalled VLC and run tests.

---

### Post by james_mcl on 2011-07-21
I've been suffering from the same problem; however I found a solution at

[http://ubuntuforums.org/showpost.php?p=11022423&postcount=7](http://ubuntuforums.org/showpost.php?p=11022423&postcount=7)

(go into Tools -> Preferences, set "Show settings" to All, go to Audio -> Output modules, choose "ALSA audio output", click on "Save".)

Apparently this is due to some sort of problem with VLC's PulseAudio support. I tried this (after completely uninstalling and reinstalling VLC) and it worked on my 64-bit Natty install.

---

