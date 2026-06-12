---
title: "Amarok"
date: 2010-10-07
forum: Multimedia Software
---

### Post by VicHF on 2010-10-07
Hello, friends. 
I've been using Ubuntu for some months now, and I'm really in love with it!
However, I'm having trouble with one of my favorite applications: Amarok.

While I run it, there is no sound in other applications like browsers or other media players. How can I solve this?

Besides this problem, there is another one: when I quit Amarok, the icon remains on the panel, but I cannot reopen nor restore it.

Thanks a lot!

---

### Post by Yellow Pasque on 2010-10-08
You need to install the KDE settings package and choose pulseaudio in the multimedia subsection for phonon's audio output. Otherwise, it will grab the audio device directly and lock everything else out.
```
sudo apt-get install --no-install-recommends systemsettings
```

---

### Post by sikander3786 on 2010-10-08
> I've been using Ubuntu for some months now, and I'm really in love with it!

Just a note:

If you were specific saying Ubuntu as the normal Ubuntu with Gnome, running Amarok seemed a bit heavier to me on my system in Gnome as it is a KDE app and needs all those libraries and stuff that is not present in Gnome by default. Thats why I reverted to Banshee, Rhythmbox and even I find Songbird lot more responsive.

If you like Amarok for any of the reasons, you can hang on with it. You can of course run Gnome apps on KDE and vice versa, just need some extra stuff and a bit extra resources.

---

### Post by VicHF on 2010-10-08
Thank you very much, friend! It's working just fine right now!

---

### Post by VicHF on 2010-10-08
Yeah, I don't want Windows anymore. Ubuntu is really nice!

Amarok is working right now, and I really had to install other packages. 
Thanks for the help, people.

---

