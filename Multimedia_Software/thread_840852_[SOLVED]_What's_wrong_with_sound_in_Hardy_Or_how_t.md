---
title: "[SOLVED] What's wrong with sound in Hardy? Or: how to edit sound files?"
date: 2008-06-25
forum: Multimedia Software
---

### Post by fsando on 2008-06-25
I'm stuck. I want to do a simple edit to a sound file but this seems to be impossible since I've installed Hardy.

Naturally first thing I did was install Audacity but Audacity has no audible output. It shows as if it works but outputs no sound. Output meters are oscillating, the pointer is moving etc.

I tried changing the output device (edit>preferences>playback) and get:
Error while opening sound device. Please check the output device settings and the project sample rate.

Now I've tried every possible combination settings in Audacity combined with settings in 'System > Preferences > Sound'. 
I've installed the 'Ubuntustudio sound package' I've updated the pulseaudio following this link
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)
Nothing has changed. 

I've gone through all the other sound apps in 'add/remove and found a rather unsatisfying solution: Install gnusound (which takes only wav-files and is clumsy to work with) install Sound Converter (lets you covert various formats into wav) - you get the picture.

My main wish is to have Audacity working. If that isn't possible I'd like a suggestion for another app that will do similar sound editing (I only need some simple cut and fade-in/out).

Thanks

---

### Post by Vivaldi Gloria on 2008-06-27
Have you tried choosing different devices in the settings menu of audacity, e.g. OSS, ALSA, etc. ?

---

### Post by fsando on 2008-06-27
Thanks for your answer. 
Yes I tried everything I could think of including that. I found the answer partly through trial and error partly from various hints around the forum (don't recall exactly where). It's a bit convoluted but worth the effort. 

Turns out the solution is to install Jack. I'm not sure if it's installed by default or it came when I installed the ubuntustudio-audio (and the ubuntustudio-plugins). 

Then you have to start the JACK Server first (from the app>sound&vid choose 'JACK Control' and click 'start') only then should you start Audacity.

In Audacity you go to Edit > Preferences and choose JACK Connection Kit as output.

If you use Amarok you can have that play through JACK at the same time too if you follow the advice given here:
[http://ubuntuforums.org/showthread.php?t=267417&page=3](http://ubuntuforums.org/showthread.php?t=267417&page=3)

JACK is absolutely a great tool - check out the other JACK tools in the "application > sound & video" menu.
I'll mark this thread as solved.

---

