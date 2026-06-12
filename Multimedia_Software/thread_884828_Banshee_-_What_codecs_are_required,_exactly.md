---
title: "Banshee - What codecs are required, exactly?"
date: 2008-08-09
forum: Multimedia Software
---

### Post by Roasted on 2008-08-09
Even after the medibuntu repository, Banshee wouldn't play.

I went to add/remove software and just clicked on a bunch of gstreamer stuff without thinking. Now, it works.

But I'm curious to know what packages in particular make Banshee function. 

Also - Anybody use Banshee and Amarok? I like Amarok, but it seems to be unusually bitchy over me being on YouTube from time to time. Like it requires me to killall amarokapp + firefox in order to get Amarok to work again... whereas Banshee and YouTube work fine, together, at the exact same time.

edit - imagine that... I set amarok to "alsa" instead of "auto detect" and now it's happy with youtube... odd. Anyway, I'm still curious about the banshee question. I kinda like this program.

---

### Post by MatthewPlanchard on 2008-08-11
I'm not one hundred percent sure.  I've got Banshee-1 installed and Ubuntu-Restricted-Extras and that's so far all the codecs I've needed.

---

### Post by timcredible on 2008-08-11
what filetypes are you trying to play?

---

### Post by silkstone on 2008-08-11
I'm not sure it answers your question as it covers more-or-less everything including java etc, rather than what you may actually need, but this is the all-purpose code I use to install everything in 32-bit Hardy...

sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libflashsupport liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs libdvdcss2 openoffice.org-java-common

---

