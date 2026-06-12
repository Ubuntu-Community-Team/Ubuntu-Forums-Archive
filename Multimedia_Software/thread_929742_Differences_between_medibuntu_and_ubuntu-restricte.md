---
title: "Differences between medibuntu and ubuntu-restricted-extras"
date: 2008-09-25
forum: Multimedia Software
---

### Post by keyshawn on 2008-09-25
I had briefly searched around for an answer on the forums, but I was wondering:

Should I install both packages from medibuntu and ubuntu-restricted-extras [hosted on multiverse, i believe] ? They both contain some of the same packages: w32codecs and libavcodec1d, for example. 

I read the [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) comprehensive multimedia howto on ubuntu forums, but it doesn't mention anything about the ubuntu-restricted-extras package. 

I understand that medibuntu has some non-free packages (where only the binaries are provided by the developers: skype, googleearth, etc), and some packages whose  functionality is crippled in the official repsitories (amarok), but I'm confused that some of the packages like w32codecs appear to be the same in both repositories and I haven't found any documentation that assures me which repository is better for users' (and my) wants and to avoid any package conflicts. 

(I plan on backing up some of my DVDs and music CDs). 

thanks,
keyshawn

---

### Post by Samanathon on 2008-09-25
Great question, though I'm not an expert, I can't see the harm in enabling both....

---

### Post by kostkon on 2008-09-25
> **keyshawn said:**
> I had briefly searched around for an answer on the forums, but I was wondering:

Should I install both packages from medibuntu and ubuntu-restricted-extras [hosted on multiverse, i believe] ? They both contain some of the same packages: w32codecs and libavcodec1d, for example. 

I read the [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) comprehensive multimedia howto on ubuntu forums, but it doesn't mention anything about the ubuntu-restricted-extras package. 

I understand that medibuntu has some non-free packages (where only the binaries are provided by the developers: skype, googleearth, etc), and some packages whose  functionality is crippled in the official repsitories (amarok), but I'm confused that some of the packages like w32codecs appear to be the same in both repositories and I haven't found any documentation that assures me which repository is better for users' (and my) wants and to avoid any package conflicts. 

(I plan on backing up some of my DVDs and music CDs). 

thanks,
keyshawn
No the w32codecs package is offered only by the Medibuntu repo.

Actually, Medibuntu is a repo whereas ubuntu-restricted-extras is a metapackage (i.e. a package that installs other packages).

Packages that may violate patents are in Medibuntu indeed.

But you are wrong, there aren't any same packages that exist in the official repos and in Medibuntu.

---

### Post by Cytomax on 2009-07-14
Thank you for the reply kostkon...
I too have the same question as the OP.
I dont know if this question has a Yes or No answer but i was kinda hoping it did...


I have ubuntu 9.04 and am wondering.....

Should i install BOTH

Medibuntu & ubuntu-restricted-extras

Or do these packages overlap in some ways and i should only install 1 of them?

Thanks in Advance
Eddie

---

### Post by igorzwx on 2009-07-14
make this:
**[Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**

[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

and relax.
All problems will be solved.

---

### Post by Cytomax on 2009-07-14
First let me start off by saying thank you to igorzwx
I appreciate your response....

I did some more searching and found what is inside each one

This is what is inside medibuntu
[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

This is what is inside ubuntu-restricted-extras
[http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras)

Now i am no linux guru but...... to me it seems that

**Ubuntu-Restricted-Extras installs**
flashplugin-nonfree
gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
libavcodec-unstripped-52
ttf-mscorefonts-installer
unrar

While

**Medibuntu installs**
# aacgain
# aacplusenc
# acroread-fonts
# alsa-firmware
# amrnb
# amrwb
# app-install-data-medibuntu
# apport-hooks-medibuntu
# gizmo5
# googleearth-data
# googleearth
# hot-babe
# ices
# libamrnb3
# libamrnb-dev
# libamrwb3
# libamrwb-dev
# libdvdcss2
# libdvdcss-dev
# medibuntu-keyring
# mencoder
# mplayer-doc
# mplayer
# mplayer-nogui
# non-free-codecs
# realplayer
# rmconverter
# skype-common
# skype
# skype-static
# skype-static-oss
# w32codecs
# w64codecs

and to me i dont see an overlap between the 2 programs even though i could be completely wrong...

Any thoughts?

Why would someone install 1 over the other or both?

Thanks in Advance
Eddie

---

### Post by mc4man on 2009-07-14
> install 1 over the other or both?

ubuntu-restricted-extras installs a set of packages that are also available to install separately from your normal ubuntu repo's (thru synaptic, apt-get or the gstreamer codec plugin.

Medibuntu doesn't install anything, it's just a repo source you enable and then install any of the available packages if desired (thru synaptic or apt-get usually

So without medibuntu enabled if you where to search say w32codecs in synaptic you'd come up empty. With it enabled you'd find it and be able to install if you wished.

---

### Post by Cytomax on 2009-07-14
That makes so much sense now... thank you for taking the time to explain it to a noob....
Eddie

---

