---
title: "pSX crashes with a segfault"
date: 2010-02-19
forum: Multimedia Software
---

### Post by xxxxme on 2010-02-19
When attempting to run [_[color=blue]pSX[/color]_](psxemulator.gazaxian.com) on Ubuntu 9.04 (and the 9.10 livecd), it crashes with a segfault.
I -have- read [_[color=blue]http://ubuntuforums.org/showthread.php?t=973021[/color]_](http://ubuntuforums.org/showthread.php?t=973021) and tried shutting down pulseaudio as recommended there.  However:
```
$ sudo /etc/init.d/pulseaudio stop
 [color=orange]*[/color] PulseAudio configured for per-user sessions
$ sudo killall pulseaudio
$ ./pSX
(pSX:6194): GtkGLExt-CRITICAL **: gtk_widget_set_gl_capability: assertion `GDK_IS_GL_CONFIG (glconfig)' failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault
$
```
This is the same error I get before shutting down pulseaudio.
How do I get pSX working?  I tried copying the psx.ini file from another machine because the thread says pSX works fine after you change the sound device used, but it still segfaults when I try running it.

---

### Post by xxxxme on 2010-02-19
Okay, so it looks like when I killed pulseaudio, it started up again immediately.  *swears at programs that are so "user friendly" that they don't do what you tell them*  I renamed /usr/bin/pulseaudio to a curse word and killed the running program again, after which I was able to run pSX and set the sound device to something besides the default.  After I renamed /usr/bin/<curse word> to pulseaudio, it was "nice" enough to restart itself immediately.

Now, pSX starts and runs.  However, the terminal constantly complains, "sound: underrun".  I haven't gotten further than just making sure pSX doesn't immediately segfault.  I'm guessing that "sound: underrun" is actually a problem I'd wish to address.  Is this so?  If that's true, what do I do about it?

---

### Post by xxxxme on 2010-02-21
Solution: Don't use Ubuntu with the Gnome desktop because someone thought it would be a good idea to patch everything to run only with PulseAudio.

Good advice from someone on IRC:  Steps to installing PulseAudio, "First, go to a psychiatrist..."

---

