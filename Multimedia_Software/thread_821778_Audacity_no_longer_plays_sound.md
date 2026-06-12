---
title: "Audacity no longer plays sound"
date: 2008-06-07
forum: Multimedia Software
---

### Post by JimmyJim on 2008-06-07
Audacity used to play sound (mp3 files to be specific) perfectly. Today, for some reason, I'm getting this error:

"Error while opening sound device. Please check the output device settings and the project sample rate."

Any ideas as to why it isn't working? I checked my playback device in Audio I/O and it is still set to OSS: dev/dsp just like before. I also tried the same mp3 files that worked before, and they aren't working, so it doesn't have to do with the mp3 files.

Any help is greatly appreciated. I am using 8.04 32-bit.

---

### Post by JimmyJim on 2008-06-07
I noticed that when Audacity is open, there is no sound at all in any application or on Ubuntu.

I really need help. Thanks in advance.

---

### Post by JimmyJim on 2008-06-07
I tried this and it worked:

In terminal after audacity has started:
killall jackd

Maybe this could explain the problem? I don't want to do this everytime to start Audacity. Plus sound doesn't work anywhere else while Audacity is open.

---

### Post by gabz8472 on 2008-06-12
> **JimmyJim said:**
> I tried this and it worked:

In terminal after audacity has started:
killall jackd

Maybe this could explain the problem? I don't want to do this everytime to start Audacity. Plus sound doesn't work anywhere else while Audacity is open.
I have the exactly the same problem and getting the same error.

"Error while opening sound device. Please check the output device settings and the project sample rate."

I'm using a lenovo Y410 with hardy.

I tried the killall jackd thing, my audio applications worked, but audacity still doesn't make a sound.

---

### Post by mastermindg on 2008-06-13
This sounds like a pulseaudio issue. Not positive, though. I just installed it. Doesn't seem to have any output modules.

One thing, though. I figured out what a lot of my problems were with sound earlier today. I had to add myself to the pulse audio groups and then restart pulseaudio. Everthing is working fine now. You may want to download pulse-tools as well.

---

