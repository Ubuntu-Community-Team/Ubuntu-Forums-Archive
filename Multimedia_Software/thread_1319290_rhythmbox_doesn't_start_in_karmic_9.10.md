---
title: "rhythmbox doesn't start in karmic 9.10"
date: 2009-11-08
forum: Multimedia Software
---

### Post by timcredible on 2009-11-08
i just installed karmic as a fresh install.  i installed digikam, devede, awn, ubuntu-restricted-extras, thunderbird, ekiga, kdenlive, libdvdcss2, ffmpeg, winff, k3b, and audacity.  Now rhythmbox doesn't run.  i think ffmpeg or audacity installed some different audio stuff than what rhythmbox wants, but i don't know what packages are messing up.  from cli, i only get this when trying to run rhythmbox:

Error re-scanning registry , child terminated by signal

which isn't very helpful.  anyone have any ideas?  thanks.

---

### Post by adoomer on 2009-11-14
I've got quite similar situation. I use fresh installed karmic for over a week, installed ubuntu-restricted-extras, audacity and some other programs and everything was working fine. Yesterday I installed kdenlive, avidemux (gtk+), Pitivi and Gnome Subtitles.
After that following programs won't run:
Brasero, Pidgin, Pitivi, Empathy, Rhythmbox, Gnome Subtitles, Totem. Except Gnome Subtitles everything worked earlier.
I tried to run Software Center, but it suddenly closes just after opening.

Running Empathy, Rhythmbox, Gnome Subtitles, Software Center, Totem using Terminal does nothing except showing this info:

Error re-scanning registry , child terminated by signal

Software Center gives more info:

~$ software-center 
(software-center:2325): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:2325): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:2325): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:2325): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:2325): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:2325): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:2325): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:2325): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:2325): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:2325): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:2325): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:2325): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:2325): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:2325): GStreamer-WARNING **: adding type gint multiple times

(software-center:2325): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:2325): GStreamer-WARNING **: adding type glong multiple times

(software-center:2325): GStreamer-WARNING **: adding type guint multiple times

(software-center:2325): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:2325): GStreamer-WARNING **: adding type gulong multiple times
Could not initialize GStreamer: B&#322;&#261;d ponownego przeszukiwania rejestru , child terminated by signal

So maybe it is in fact a problem with GStreamer?

---

### Post by Jbike on 2009-11-14
I have two systems (very different hardware) that do the same thing as described above!!

 I also recently installed the restricted extras pkgs , libdvdread4 and I enabled the following from software sources:  

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner and 
Akirad Repository - Main   


Here is a clip from opening empathy from a terminal: 

    [I][COLOR="Red"]jbike@jbike-desktop:~$ empathy
Error re-scanning registry , child terminated by signal
Run 'empathy --help' to see a full list of available command line options.

(empathy:3941): empathy-WARNING **: Error in empathy init: Error re-scanning registry , child terminated by signal
jbike@jbike-desktop:~$ 
[/COLOR][/I]

As mentioned above, other packages also do not work. 

Any ideas anyone?

Thanks, Jbike

---

### Post by Jbike on 2009-11-14
Also... both of my systems were running compiz, both have nvidia graphic cards (one the fx6200, the other fx5200).

Ideas anyone? 

Thanks,
Jbike

---

### Post by timcredible on 2009-11-15
i just went back to 9.04.  too many issues with 9.10

---

### Post by Jbike on 2009-11-16
I just fixed rhythmbox, empathy, brasero by following the instructions at: [COLOR="Red"]http://www.insidesocal.com/click/2009/11/ubuntu-karmic-fail-pidgin-and.html[/COLOR], though,  one of the mentioned packages to reinstall was not present in any of my active repos. Here is a summary of the instructions:

[COLOR="Red"]Let's review: If Pidgin, Empathy, Rhythmbox, Brasero and Totem are not running on your Ubuntu 9.10 system, first update the box, then use the Synaptic Package Manager to remove frei0r-plugins and reinstall libcv1, libhihgui1 and libcvaux1.

[/COLOR]

I reinstalled libhal1 instead of libhighuil... all of the packages work, including kdenlive and cinelerra. 

I am sure that this makes sense to someone. 

Jbike

---

### Post by adoomer on 2009-11-16
Great solution. After removing frei0r-plugins everything is working great. This missing package in your repos is only an effect of a typo: it's not [COLOR=Red]"[/COLOR][COLOR=Red]libhihgui1" [/COLOR]but [COLOR=Red]"libhighgui1". [/COLOR]Thanks for help!

---

### Post by Chew55 on 2009-12-27
I've done everything thats recommended in this thread and the problem persists.

The frei0-plugins weren't installed when I started either.

Any one else got any ideas?

---

### Post by robert-km on 2010-01-13
> **Chew55 said:**
> 
Any one else got any ideas?

Maybe You should try to remove openshot-frei0r.
It was solution for my problem.

---

