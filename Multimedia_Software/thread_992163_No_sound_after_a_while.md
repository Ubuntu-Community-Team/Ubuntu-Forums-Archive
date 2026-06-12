---
title: "No sound after a while"
date: 2008-11-24
forum: Multimedia Software
---

### Post by christianxxx on 2008-11-24
I can see from the forums that sound really is a hot issue.
However, I cannot find this particular problem, so here goes:

I'm running a clean installation of Ubuntu 8.10. Sound works fine for a while, then suddenly no sound from any application. When it stops working, the following is observed:
- Obsiously, no sound what so ever
- 2 zombie-state processes of aplay
- Flash videos usually freezes during the first 10 seconds
- Testing sound from the sound preferences produces the following error:
"audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Failed to connect: Connection refused"

It can be resolved with a reboot, but after a while it's the same.

I've tried a few solutions to sound problems, but none of them seem to help. This card and default sound setup worked flawlessly in 8.04, but improved support for my wireless was a good reason for upgrading to 8.10.

I hope someone can point me to a permanent solution for his interesting problem.

---

### Post by psyke83 on 2008-11-24
> **christianxxx said:**
> I hope someone can point me to a permanent solution for his interesting problem.

Your problem is that the PulseAudio daemon is crashing on your system after some time.

I have a feeling that your sound card is not reacting well to the fragment size (buffering) tweaks in Intrepid's PulseAudio configuration.

First of all, follow these steps to ensure a perfect PulseAudio setup: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Secondly, look at the question regarding stuttering in Appendix B.

Instead of changing the fragment size and amounts, comment those lines entirely (this will force PulseAudio to use its internal defaults). In other words, change:

```
default-fragments = 8
default-fragment-size-msec = 10
```

...to:

```
; default-fragments = 8
; default-fragment-size-msec = 10
```

Log out and back in for changes to take effect. Hopefully PulseAudio will no longer crash on your system.

---

### Post by christianxxx on 2008-11-25
Thanks for trying, but this actually didn't solve it.
I've found a way to restart the PulseAudio daemon without rebooting. It's a little tricky as there are some files involved. To further complicate matters, running programs is referencing the old and dead PulseAudio, so they have to be restarted.

But I'm going to run PA in verbose mode and see if I can see exactly what happens when it crashes.
I'll post back later.

---

### Post by _sphinx_ on 2009-02-24
Any progess geeks?
I am facing exactly the same problem.

---

### Post by noisufnoc on 2009-02-24
Subscribed to this...I'm seeing the same issue on my system.

Can you post details on how to restart the deamon?

---

### Post by markbuntu on 2009-02-24
You can start the pulseaudio daemon with

pulseaudio -D

If you are having problems with pulse crashing you can start it with

pulseaudio -vvv

this will print to the terminal all the pulseaudio messages which can pinpoint the problem and would be extremely helpful in a bug report.

---

### Post by geezerone on 2009-03-19
Have had similar problem in Hardy for some time so watching this space for a solution too.

---

### Post by oniichan on 2009-03-19
Audio just stopped on 8.10 (on a Dell Inspiron 6000). There were no software or config changes. It just stopped. Reinstalled pulseaudio - no effect. Ran kernels v12, 13, and the new 14 with no change.

~ >> pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.

Thanks for any help....

---

### Post by oniichan on 2009-03-19
OK.Mine's fixed and hopefully it will help you. Apparently some update changed the group permissions for 'pulse', 'pulse-access', and 'pulse-rt'. Go to System-Administration-Users and Groups. Unlock the user settings (button lower right) and click on 'Manage Groups'. Double click on each group and make sure both your user and the root are selected. Now re-boot and the daemon should start properly thus restorirng your audio.

On the otherhand,if problems persist.Please follow this excellent short help file:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

Whoever wrote this deserves a kiss. Follow his procedure scrupulously and hopefully this will repair any other inadvertent changes (in my case many of the drivers were muted?!?!).

Anyway again, hope this helps.

---

### Post by daydbai on 2009-03-19
Oniichan.... thanks for the tip - I also have a 6000 and have had the same problem.  
Interestingly, my wireless card also randomly stopped working.. has this happened to you as well?

Thanks

---

### Post by oniichan on 2009-03-19
Hi. Never had a problem with my wireless card on my Inspiron 6000 using 8.10. Go to the Dell Support Forum to search for an answer. There is a complete how-to there which should get you working. Hopefully this thread can be closed. It appears everyone in this thread has a permission problem and this should be the fix.

---

### Post by darreld on 2009-03-20
It appears the groups fix has done the trick, although it's only been 24 hours ;)

Thanks for the help

-darrel

---

