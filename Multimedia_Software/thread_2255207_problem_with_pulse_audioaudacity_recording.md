---
title: "problem with pulse audio/audacity recording"
date: 2014-12-03
forum: Multimedia Software
---

### Post by 118118 on 2014-12-03
sound settings say register the line in, at the necessary volume.

but when i set to pulse audio, and ask audacity to record, i get garbled sound and the recording does not proceed at normal speed, but much slower taking a few seconds to record a second of audio.

any help ?

---

### Post by carlwsnyder on 2014-12-03
This is a long known problem, and seems to be related to a design choice in Audacity.  The fix seems to be to use the ALSA sound system, not pulse-Audio.  I have seen the same complaints since 8.04 Hardy Heron, when PA was introduced.

---

### Post by 118118 on 2014-12-05
hi

how do i set that up, please :) ?

thanks man.

edit none of the options on right hand drop down menu capture line in audio. i am running 14.04 / 2.0[COLOR=#545454][FONT=arial]5[/FONT][/COLOR]

---

### Post by haplorrhine on 2014-12-05
Uninstalling PulseAudio and instead relying *solely* on alsamixer will bypass PulseAudio bugs , but I couldn't get Audacity to record through alsamixer.  I suggest reinstalling PulseAudio first.

In my case, the bug kept returning with each reinstall until I selected "Downlaod updates while installing".

---

### Post by wamses2 on 2014-12-06
> **118118 said:**
> hi

how do i set that up, please :) ?

thanks man.

edit none of the options on right hand drop down menu capture line in audio. i am running 14.04 / 2.0[COLOR=#545454][FONT=arial]5[/FONT][/COLOR]

Try this in a terminal:
sudo apt-get install alsa-utils

After a bit of faffing around I managed to get audacity recording OK through a mic (via a Behringer mixer) and also recording online radio etc.
I found it necessary to keep an eye on the levels of alsa since they tend to change (I don't know why), you can do this once it's installed by the terminal command
alsamixer

I usually do this before I start any recording

Good luck, you will get there in the end

---

### Post by Rob Sayer on 2014-12-06
You may also want gnome-alsamixer unless you're running KDE, which isn't a gtk/gnome based DE.

I've found even with media playing software that some work better with the alsa output module, others pulse.

Whatever you do, *do not uninstall* pulseaudio.  I don't know how that ended up on so many crap blogs but it's a bad idea.  Pulse has a ton of dependencies and you'll just make your system unstable.  If you actually do have to disable pulse ... which I doubt here very much ... there are better ways to do it.

---

### Post by haplorrhine on 2014-12-06
You read crappy blogs when you can't find anything better for your problem. :)

---

### Post by Rob Sayer on 2014-12-07
> **haplorrhine said:**
> You read crappy blogs when you can't find anything better for your problem. :)

I know.  It's hard at first to tell what's good or bad.  I was lucky because I had some background before installing linux and I had problems sorting out info at first.

The main things I'd suggest for beginners qwith this stuff are:

Don't do it unless it specifically says it's for your release of your distro.  What worked for 13.10 may very well not work for 14.04.

Don't do it if there's nothing saying how to undo the changes if they don't work.

Only change one thing at a time.

---

### Post by 118118 on 2014-12-18
i have alsa mixer installed, and can set levels easily enough but how do i set up audacity to use alsa

---

### Post by Rob Sayer on 2014-12-20
I'm using my netbook now which doesn't have audacity installed, and this isn't something I know off the top of my head.  But have you tried audacity preferences?  There should be a module selection in there somewhere.

Also, search the audacity forums.

---

### Post by Rob Sayer on 2014-12-20
One more thing I just thought of ... if you want to avoid crappy blog syndrome, don't use Google as a search engine.  It'll give preference to sites with google powered ads on them.  Like most crap blogs.

I almost always use startpage HTTPS, occasionally duckduckgo.  This netbook is actually running mint with the mate DE, and their firefox default install doesn't include google as a search engine.  I don't intend to install the plugin either.

Actually I don't even use Google when using Chrome ... yup, startpage HTTPS ... which is safer than startpage HTTP BTW.

This way I get pointed largely straight to here or askubuntu when I want to look something ubuntu up.

---

### Post by Bucky Ball on 2014-12-20
*Thread moved to **Multimedia**.*

---

