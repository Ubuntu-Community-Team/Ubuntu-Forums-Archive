---
title: "Uninstall PulseAudio"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by chimerical_brio on 2007-11-05
I've heard good things about PulseAudio, so when I installed Gutsy, I sudo apt-get'ed pulseaudio. It tried to configure itself, and I got some errors, but I  figured it wasn't a big deal. Sound from pretty much everything except MPlayer stopped working, but it wasn't until today, when I read the article on PulseAudio on linux.com, that I realized that the reason my sound stopped working, when it had worked before, is that PulseAudio screwed it up. Replaced ESD or something. Anyway, is there any (easy) way to reconfigure my sound so it'll work? I'd really rather not reinstall Gutsy...how do I just uninstall PulseAudio and make my sound work? Thanks a lot.

---

### Post by qamelian on 2007-11-05
Without knowing the exact steps you went through  to setup pulseaudio, it might be tricky to help you reverse the process. The fact that it removed esd is no surprise though as it is intended to replace esd entirely. Eventually, Gnome will drop esd altogether.

You might want to take a look at the link below. It may not help you get back to esd, but it might help you get pulseaudio working to your satisfaction.

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

### Post by logos34 on 2007-11-05
I too would like to use pulseaudio...it's definitely superior to the current enlightenment sound server which it will at some point replace.  It works fine with audacious and amarok.  But I need RealAudio support, nor does it seem to be an option with MediaCoder or mp3directcut on Wine...Mplayer seems to be a problem too (I don't want to have to recompile with the patch)...Oh, and it I think it also killed my sound file preview function (.ogg at least), so until it's ready for primetime I'll stick with the default.

But here's a thread that might interest you:
[http://ubuntuforums.org/showthread.php?t=599334](http://ubuntuforums.org/showthread.php?t=599334)

If you decide to uninstall I think all you need to do is:
[B]
sudo apt-get install esound[/B]

(-->it will automatically pull out **pulseaudio-esound-compat**, which conflicts).

and
**sudo apt-get remove pulseaudio**

---

### Post by rykel on 2007-11-05
Hi all,

I do not have sound on my system too... if pulseaudio is so unstable yet, why do we use it so soon?

Anyway, can any of you advise me on what to do to retrieve my sounds?

---

### Post by logos34 on 2007-11-05
> **rykel said:**
> Hi all,

I do not have sound on my system too... if pulseaudio is so unstable yet, why do we use it so soon?

Anyway, can any of you advise me on what to do to retrieve my sounds?

Start here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by chimerical_brio on 2007-11-05
Wow...turns out I just had to unmute my headphones/PC speakers under alsamixer to get it to work. Which seems totally wrong since MPlayer had sound, but oh well, everything works now.

---

