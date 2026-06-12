---
title: "HDMI not working after upgrade to 13.04"
date: 2013-05-01
forum: Multimedia Software
---

### Post by sidewayssammich on 2013-05-01
Hi. Sorry if this is in te wrong section or been asked before. Since I upgraded to 13.04, my HDMI out doesn't work. The screen has lots of bars or is totally green, or some other wird pattern. It doesn't show any hint of whats meant to be displayed. I can confirm that this is not the cable. Is there a fix for this?

---

### Post by Ed Tignor on 2013-05-03
Exactly same problem.  I am using the other digital output of my video card, but would like to switch back to the HDMI if possible.

---

### Post by skeve on 2013-05-04
[http://ubuntuforums.org/showthread.php?t=2141888&p=12632616#post12632616](http://ubuntuforums.org/showthread.php?t=2141888&p=12632616#post12632616)

upd. sorry, it seems that's not the answer for your problem

---

### Post by Mark Phelps on 2013-05-04
Hey folks ... we're not mind readers here!  How about some info about the following: (1) what version of Ubuntu you upgraded FROM, (2) what make and model video card you're using, (3) what video drivers you used before (restricted or open-source)?

---

### Post by baslow on 2013-05-06
I am having the same problem.  Posted [details here]("http://ubuntuforums.org/showthread.php?t=2140872")

---

### Post by baslow on 2013-05-06
I've found [this post]("http://ux51vz.blogspot.com/2013/04/how-to-install-nvidia-31912-drivers.html") about what seems to be the same problem. While it suggests that installation of something called [Bumblebee ]("http://www.webupd8.org/2013/02/bumblebee-31-released-with-primus.html") might solve the problem the poster favors the installation of a recent beta nVidia driver (nvidia 319.12) as a better solution.  He points to this ( "dirty" ) method of getting that driver installed: [http://paste.ubuntu.com/5601226/](http://paste.ubuntu.com/5601226/) 

I don't really understand a lot of this.  I gather that Nvidia provides a technology called [Optimus ]("http://en.wikipedia.org/wiki/Nvidia_Optimus"), originally intended for laptops but now marketed for desktops under the name "Synergy".  To minimize power usage, Optimus switches the kind of graphics processing used depending on the nature of the task -- so that it only uses its more energy-intensive heavy guns when they are necessary.  The technology has been released in easy-to-install packages for Windows and Mac but is [not yet fully supported under Linux]("http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html") (which is why it's necessary to install the beta).  But I don't understand what any of this has to do with the card being able to detect an HDMI display.

I am now working up the nerve to try implementing the "dirty" solution mentioned above. Any helpful observations or comments (or words of warning, for that matter) would be welcome.

---

