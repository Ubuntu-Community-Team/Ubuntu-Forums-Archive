---
title: "Openshot borks my video"
date: 2009-11-10
forum: Multimedia Software
---

### Post by afrodeity on 2009-11-10
Fresh install of Karmic. Was admiring it. Downloaded one or two codecs, then installed VLC and Realplayer and then Openshot, thinking I could get some video editing done. No go. It has a weird effect on ffmeg and gstreamer. Tried installing all the codecs as per Comprehensive Multimedia FAQ, but now can't play my wmv's and flvs. Get the following in mplayer;

```
Internal Data Stream Error
```

or

```
Gstreamer encountered a general stream error
``` for mp4s.

Its the first time I've ever used Realplayer on linux so it might be related somehow, will uninstall. I uninstalled Openshot, but no luck.

UPDATE: Okay, I uninstalled realplayer but still nothing. Video is O'rrible.

---

### Post by mc4man on 2009-11-10
What you may wish to expand on is how did you install openshot, from a .deb or did you add the openshot ppa?

---

### Post by MooseDog on 2009-11-10
I had the exact same problem afrodeity.  SOme Googling and searching 'round here revealed that the developer **completely replaced many codecs and libraries** on your install so that his program could work.  Net result is that many of your previously installed progs no longer do.  Case in point.

There's several different options out there on how to fix this, I haven't figured out the right one nor how, but SHAMEFULLY not a word from the developer himself.  Not even an admission that **he** borked **your** system. (and mine), except perhaps in passing in his latest post.

So currently, I'll never use his package and am currently avoiding Ubuntu until I can get around to a new install.

---

### Post by mc4man on 2009-11-10
If you added the openshot ppa then this should square you up again

[http://ubuntuforums.org/showthread.php?p=8046291#post8046291](http://ubuntuforums.org/showthread.php?p=8046291#post8046291)

---

### Post by afrodeity on 2009-11-11
Stupidly I added the deb [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu) karmic main ppa. But in his posting he seemed to assure people that any conflicts with VLC etc had been resolved. Worse than a conflict, total bork.

UPDATE: Problem solved. Pity, I was hoping Openshot would be THE video editor in a world without great video editors. One can only hope for the best and a drag-and-drop multimedia suite that has a common interface like iPhoto, iMovie etc. Common libraries with codecs that don't conflict!!!!!!

---

### Post by mc4man on 2009-11-11
That openshot ppa doesn't seem to bad ( the other one had ffmpeg packages that were guaranteed to  be bad (openshot-developers ppa) and still are.

( though the page i found for yours is in french I believe, so can't totally understand some of the warning - seems to be about video display issues..??

> Un bogue non propre à Openshot mais sur MLT et concernant les systèmes 32 bits provoquent un bug d'affichage: apparition de lignes verticales vertes, blanches ou roses qui pour certaines personnes sont résolues par la désactivation de Compiz, solution provisoire en attendant une nouvelle version de MLT.  

Did you totally remove the python-mlt packages also..?

going to add that repo to a tester and see, by all rights it shouldn't harm things - only has openshot and mlt packages


will let you know.

---

### Post by afrodeity on 2009-11-11
I see there's an issue with the legality of Openshot codecs [https://answers.launchpad.net/openshot/+faq/723](https://answers.launchpad.net/openshot/+faq/723)

I don't see how installing the "stripped" versions, would be the overall solution, since these are the codecs in universe which Openshot installs as default and which are the source of the problem. If Openshot was even working fine, would be another story, but the video preview was weird.

Any suggestions on a workaround that will allow us to install Openshot without killing Mplayer and VLC?

---

### Post by mc4man on 2009-11-11
> .....see there's an issue with the legality of Openshot codecs...


I believe that's about the openshot developers ppa which would replace your ffmpeg libraries with it's own. 

It was using the so called 'un-stripped or extra versions' of the ffmpeg libs, personally don't see the issue there, as far as legal hassles for end users, for personal use don't think there are any. 

If you're distributing video encoded with libx264 I don't have a clue.

The real issue was/is that their ffmpeg build and packaging is not compatible with the repo apps that also use ffmpeg libs.

As far as the ppa you linked to it doesn't touch any ffmpeg libs though it probably needs the extra versions of the ffmpeg libs to work well.

Here's the control file for the openshot .deb
> Depends: python, python-xdg, python-gtk2, python-glade2, python-pygoocanvas, libgoocanvas3, libgoocanvas-common, mlt-python, libmlt1, libmlt++2, frei0r-plugins, sox
Suggests: openshot-doc

So as bad as the other ppa was, at first glance this one seems ok.

Openshot installed and opens fine, vlc still plays audio and video as before - tried various including m4a, mp4, avi with xvid, h263, h264 video, no change.

Will leave on tester and see if anything occurs

Edit:
This is every thing installed when installing openshot from the edge ppa on a relativity fresh install in case you wish to remove all that may have been installed along with it.
> installed the following packages:
[COLOR="Blue"]frei0r-plugins (1.1.22git20090409+repack-0ubuntu1)[/COLOR]
libcv1 (1.0.0-6.2ubuntu1)
libcvaux1 (1.0.0-6.2ubuntu1)
libgavl1 (1.1.0-2)
libgoocanvas-common (0.15-0ubuntu1)
libgoocanvas3 (0.15-0ubuntu1)
libhighgui1 (1.0.0-6.2ubuntu1)
libmlt++2 (0.4.4-2build1)
libmlt-data (0.4.4-2build1)
libmlt1 (0.4.4-2build1)
[COLOR="Blue"]libsdl1.2debian-pulseaudio (1.2.13-4ubuntu4)
libsox-fmt-alsa (14.3.0-1build1)
libsox-fmt-base (14.3.0-1build1)
libsox1a (14.3.0-1build1)[/COLOR]
mlt-python (0.4.7e-0ubuntu4~ppa1k)
openshot (0.9.53-0ubuntu4~ppa1k)
python-pygoocanvas (0.14.1-0ubuntu1)
[COLOR="Blue"]sox (14.3.0-1build1)[/COLOR]


blue are quite innocuous

---

### Post by MooseDog on 2009-11-11
thx 4 the research mc4man.  quick q: does installing from the new launchpad ppa 'fix' what the old deb install borked?  that's great it works as a fresh install, congrats to the developer, but fixing what he messed up is a concern.

---

