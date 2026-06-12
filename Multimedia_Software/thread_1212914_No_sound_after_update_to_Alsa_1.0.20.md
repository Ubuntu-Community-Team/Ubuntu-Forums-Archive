---
title: "No sound after update to Alsa 1.0.20"
date: 2009-07-14
forum: Multimedia Software
---

### Post by Jarige on 2009-07-14
I installed Ubuntu 9.04 on my cousins laptop. It worked perfectly, except for the Microphone. Well, my brother has exactly the same laptop, and I fixed the mic there using Alsa 1.0.14. 
When I wanted to do the same on my cousins laptop I found out that Alsa 1.0.20 was out already, so I installed that version.
I used to test the microphone with Skype using 2 computers. The pdd thing was, that whatever I spoke into cousins laptop's mic, came to the other end eventually. Only problem was that it came about **1 minute** later. Sound worked perfectly back then. But when I left my cousin's home, his sound didn't work anymore.

How do I install Alsa 1.0.14 again, and completely removing 1.0.20?
Or; how do I turn every sound settings back to the original state after installing so I can manually install Alsa 1.0.14 again?
Or; is there a new Alsa version which might fix this problem?

---

### Post by Jarige on 2009-07-14
Forgot to say that I'm going on vacation for about 2 weeks from now, so I won't be able to reply. I would be happy to reply in 2 weeks :)

---

### Post by igorzwx on 2009-07-14
If your laptop is not very new, you would not be able to use Skype with
PulseAudio.
I soved the problem by installing OSS4 (see Ubuntu documentation).
Now my Skype and Ekiga work perfectly.
Fantastic performance.

---

### Post by Jarige on 2009-07-14
Its one year old, and as I said, it didn't work with Pulse Audio.
I have solved the problem, I just don't know how to uninstall Alsa 1.0.20 which I installed from source code :)

---

### Post by igorzwx on 2009-07-14
Can you explain in a more understandable way.

Perhaps, you may need to blacklist ALSA modules.

I am using ALSA drivers with OSS4
You can fix playback of some ALSA apps in this way.

---

### Post by Jarige on 2009-07-14
I mean that I have solved the problem on my brother's laptop, with exactly the same hardware, but not on my cousin's laptop. And thats because I installed different Alsa versions on both the laptops. 1.0.14 working, 1.0.20 not working. Exactly the same laptops.
I do not know what OSS4 is :)

---

### Post by igorzwx on 2009-07-14
Do you want to try?

---

### Post by Jarige on 2009-07-14
If you tell me how to. If you really think thats the best thing to do, then I'll do it. But as I said, I'm leaving in a few hours. I won't be available for 2 weeks as of today.
And, another thing. I do not have the laptop right now, I cannot reach it, cause its not mine. I just created this topic for him, cause he couldn't.
Cya in 2 weeks :)

---

### Post by igorzwx on 2009-07-14
USB audio devices are not supported, and something else too.
But I am happy with OSS4

If you have Ubuntu 9.04, it is very simple (there is deb to install)

Read this:
[http://ubuntuforums.org/showthread.php?t=1212887](http://ubuntuforums.org/showthread.php?t=1212887)

do it carefully
better try first on the old box

---

