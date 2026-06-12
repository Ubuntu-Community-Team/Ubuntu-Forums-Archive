---
title: "Mandriva 2009 RC!"
date: 2008-09-05
forum: Mandriva/Mageia
---

### Post by bartos on 2008-09-05
Just playing with RC1 gnome also.. They finally fixed the JMicron problem. I always had to disconnect all other drives except the one I was installing to or installer would crash.
I know they are changeing Printerdrake but I don't see an option in any menu or MCC to install a printer.Bug 43295 Have to install it all first.
Wow software manager is fast now
This could be a hard toss up between M 2009 and Lenny as the this decision will last me two years.

---

### Post by pelle.k on 2008-09-05
I installed both the (free!) gnome and kde desktop.

KDE4;
Nice! I could certainly get used to this. KDE is still a bit buggy though.
The mandriva work is a bit rough around the edges, such as misc gnome applications installed by default (totem etc), no automatic codec suggestions (phonon is running gstreamer, so just install the gstreamer decoders package), Nvidia driver can be installed from drakconfig only if you update from the command line first (urpmi --auto-select).
Also, personally, i don't think "ia ora" fits kde4 very good. Isn't it time for a new theme default btw?
In the end, impressive work, and i imagine it will be a nice setup by the time of the release. KDE4 has never been this stable for me.

Gnome;
Holy crap! Is this a development version?! I didn't stumble on one single bug during my testing (only a few hours mind you). However, there was no thorough stress tests involved.
Now, what i didn't like, was the long (horror) list of gnome "session" startup programs. This is what i tried to get away from when leaving windows (more or less) a couple of years ago. It seems it's growing larger with every release.
*Personal note; they should make this preference more visible, but leave the decision of whether items should be activated by default up to the end user*

drakconfig is particulary snappy in 2009. It starts up in less than a second. (thumbs up).
And who doesn't like the new dependency removal upon uninstalling packages, "debian style".
Also, my system clock remain unchanged (unless i do it myself, naturally) unlike the nasty bug from 2008 (and 2008.1) that would do it for you every now and again against your will!

---

### Post by ffi on 2008-09-10
> **pelle.k said:**
> 
The mandriva work is a bit rough around the edges, such as misc gnome applications installed by default (totem etc), no automatic codec suggestions (phonon is running gstreamer, so just install the gstreamer decoders package)

The reason totem is installed is because of fluendo, the legal codec solution for linux but codeina also suggests plf (and it works here); I started a movie and codeina popped up asking me to install plf of fluendo codecs...

> Nvidia driver can be installed from drakconfig only if you update from the command line first (urpmi --auto-select).

automatically installed and set up after running XFdrake
>  
Also, personally, i don't think "ia ora" fits kde4 very good. Isn't it time for a new theme default btw?

yeah agree


> drakconfig is particulary snappy in 2009. It starts up in less than a second. (thumbs up).

Finally it doesnt look for and tries to insert the floppy controller anymore, if in 2008.1 you delete the kernel floppy module it starts up in a second too.

> Also, my system clock remain unchanged (unless i do it myself, naturally) unlike the nasty bug from 2008 (and 2008.1) that would do it for you every now and again against your will! yeah I have seen that for a while (2008.1 but not on every system)

---

