---
title: "CODECS Won't Load"
date: 2010-03-23
forum: Multimedia Software
---

### Post by bitec on 2010-03-23
Greetings fellow ubuntu lovers

I have just reinstalled ubuntu 9.10 on my laptop. The laptop is used as a Jukebox and has never had a problem doing this job. Yesterday my HDD died, hence the reinstall. When I go to add the MP3s to rythumbox and it searches for the relevant codecs it keeps saying "No packages with the requested plug ins found". I have been to the ubuntu restricted extras site to DL the package and I get a  "URL failed to load" message. So I go to an unsupported site and DL the package and install it manually but I still can't add any MP3s. Now it is saying that the restricted extras package is already loaded but I still can't add any MP3s.....Please help.....

---

### Post by boombox1387 on 2010-03-23
Not sure if I can help or not, but...

If you go to System > Administration > Software Sources, which boxes are checked in that first tab?  You'll probably want all four (main, universe, restricted, multiverse).  If they aren't all checked, check them, then close the software sources.  Next go to System > Administration > Synaptic Package Manager.  While there, search for 'gstreamer' and make sure you have installed:

libgstreamer0.10-0
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly

If this works, great!  If not:

Can you play other formats, like .ogg (or .oga) and .flac?  Can you play mp3s in other linux media players, such as Banshee or Amarok?

As a general tip, you might find [Ubuntu Tweak]("http://ubuntu-tweak.com/") to be a much easier way to set up a new installation (rather than searching online for packages).  It makes initial tweaks and configurations pretty simple, and it's really easy to use Tweak to install the Ubuntu Restricted Extras packages that should provide mp3 playback.

---

