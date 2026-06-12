---
title: "Sounds capture crashes X windows!"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by tedrogers on 2006-11-29
Hi,

This is really weird and I only noticed it when I tried using Skype and no-one could hear me!

I'm using an IBM T22 with inbuilt microphone.

Now, I can activate the microphone, add 20db boost and so forth. I can actually get it to feedback if I put the volume loud enough....so I KNOW it is working.

But, when using the ALSA driver or OSS driver it doesn't actually record anything. I've tried with the basic sound recorder in Edgy and things like Audacity...but still no joy.

If I go into the sound preferences, and mess about with settings, especially ones relating to the mic, then it freezes the mixer. I can force quit this, but then if I go into it again, it freezes X windows. I can restart X with CTRL+ALT+DELETE to get back to the log-in screen, but then it gives me an error saying something like 'the login is crashing, trying alternative' and I get a different log-in screen. If I log in here the whole X window system hangs. I have to do a CTRL+ALT+F1, then do a manual login and execute sudo shutdown -r now....nothing else works (that I know of!)

Also if I go into the Sound option in System > Preferences, all of the tests work, except for the sound capture option at the bottom in Audio Conferencing....and guess what....this freezes X and were back where we started again.

This is doing my head in now and I've tried everything I can think of....including reinstalling alsa-base, alsa-utils etc etc.

Has anyone got any ideas here?

Thanks.

---

### Post by wieman01 on 2006-11-29
Have you tried "alsamixer" or similar from command line (not in front of my own computer)? You can actually configure your sound settings (includ. the microphone) there. I'll check tonight which setting it is. "Tab" lets you change screens in "alsamixer" for other settings. Check it out yourself.

---

### Post by tedrogers on 2006-11-30
> **wieman01 said:**
> Have you tried "alsamixer" or similar from command line (not in front of my own computer)? You can actually configure your sound settings (includ. the microphone) there. I'll check tonight which setting it is. "Tab" lets you change screens in "alsamixer" for other settings. Check it out yourself.

Hi Wieman,

I have since totally desroyed/broken my installation by running the commands found of the edgy wiki:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME)

When I first ran this it made no difference, so I tried to backtrack what I had done, i.e. putting the backup file back instead of the modified one, deleting any files I had created and finally changing this code from this:

```
sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

To this (and running it):

```
sudo ln -fs /usr/lib/libesd.so.1 /usr/lib/libesd.so.0
```

Basically I swapped the 0's and 1's around.

After I rebooted my system won't load X anymore.

I have got a backup (thankfully), but if I can fix this I would rather do that.

Can you advise here?

Thanks.

---

### Post by tedrogers on 2006-11-30
I couldn't live without Ubuntu so I restored from a backup.

Now I just gotta put everything back as it was before.

Ho hum.

And what's worse is the problem is still there. As soon as I go anywhere near the sound mixer, it hangs X windows....but mainly the top bar...the main desktop still works and I can click/right-click etc.

alsamixer doesn't do what I want...it won't enable recording from my mic even though capture is selected beneath it.

Any ideas?

---

### Post by wieman01 on 2006-11-30
Hi Ted, 

What ISO image have you used to install Ubuntu? Have you ever tried the "alternate" version of Ubuntu? Perhaps that resolves your problems. Seen this before.

[http://ubuntu-releases.cs.umn.edu//6.06/]("http://ubuntu-releases.cs.umn.edu//6.06/")

---

### Post by tedrogers on 2006-11-30
Hi Helge,

I had to use the alternate CD to install on this system as the live CD/DVD would not work. This is because the gfx on this T22 is really bad (S3 Savage only 8192 bytes) and live CD just won't boot into X.

On Dapper the text-based installer was on the main CD (as I recall), but in edgy they put it on the alternate disc.

So...in short...I'm already there!

Cheers.

---

### Post by wieman01 on 2006-11-30
Then I'd try Dapper instead. Edgy may be to experimental for an old T22. Really, go for Dapper LTS & I am sure you'll be fine...

---

### Post by tedrogers on 2006-12-01
I'll do another backup tonight and give it a go.

---

