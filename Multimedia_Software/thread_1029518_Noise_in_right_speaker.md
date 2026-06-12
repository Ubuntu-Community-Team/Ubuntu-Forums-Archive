---
title: "Noise in right speaker"
date: 2009-01-03
forum: Multimedia Software
---

### Post by WailingWailer on 2009-01-03
I have one strange problem and guide in sticky doesn't work for me. I had kubuntu 8.04 and i have completely formatted disk and now i have xubuntu 8.10 and I still have the same problem: When playing music or any sound (in any movie or music player) I hear noise in my right speaker. There is no noise in left speaker but it's much more quiet than right. What can I do?

---

### Post by gettinoriginal on 2009-01-03
Can you check out other speakers ??  Sounds like the right one might be bad.  Since you have already tried the wiki, you can also try "advanced search" putting in "speaker noise" and checking title only.

---

### Post by WailingWailer on 2009-01-03
It isn't problem with the speakers - they work fine in winxp.

---

### Post by sendblink23 on 2009-01-03
> **WailingWailer said:**
> It isn't problem with the speakers - they work fine in winxp.

Try inserting Headphones... if you still have that issue on your *RIGHT headphone...  well then in that case it is a *Linux Issue

If you dont have that *weird sound noise.. on your Headphones at all.. then the Obvious.. get new speakers


Just try that out...  *headphones  or Someone to lend you other speakers (you don't have to install anything ... just connect them

---

### Post by WailingWailer on 2009-01-04
I forgot to tell - sometimes they work fine, like today - but I don't know why they don't work always. But it's definitely nothing wrong with speakers - if i switch right and left there is still noise (but in other speaker).

---

### Post by sendblink23 on 2009-01-04
> **WailingWailer said:**
> I forgot to tell - sometimes they work fine, like today - but I don't know why they don't work always. But it's definitely nothing wrong with speakers - if i switch right and left there is still noise (but in other speaker).

Did you test with HEADPHONES... like I mentioned??  And Also connecting other Speakers in your computer (not using the ones you have)

---

### Post by gettinoriginal on 2009-01-04
Definitely a hardware problem, possibly your sound card is going ??

---

### Post by sendblink23 on 2009-01-04
> **gettinoriginal said:**
> Definitely a hardware problem, possibly your sound card is going ??

Yeah thats what I want him to figure out..  by testing using headphones & connecting other speakers .. to see his outcome of those.

---

### Post by MasherTheMash on 2009-01-16
I've got a sound issue, left channel is fine but on occasions the right channel will have a crackle. Strange that it only happens every now and again. I'm using Ubuntu 8.10,not sure if Pulseaudio is something to do with it as it didn't do it on 8.04.

---

### Post by WailingWailer on 2009-01-16
It happens on headphones too.

---

### Post by MasherTheMash on 2009-01-19
Taken from a bug report on launchpad:

"The possible solution is to replace the following 3 lines in /etc/pulse/daemon.conf:
; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

With:
default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 2

Either, it works for me yet. And after several reboots too"

Seems to have worked for me too!! 3 restarts and no crackle!!

---

### Post by WailingWailer on 2009-01-23
I don't have this file ... :( Any other solution?

---

### Post by WailingWailer on 2009-01-31
Any ideas, at least?

---

