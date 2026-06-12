---
title: "Cpu jumps up 80% when playing video"
date: 2009-11-27
forum: Multimedia Software
---

### Post by jonny_bowes on 2009-11-27
Hi,I've been having problems playing flash and it using up all my CPU but even more strangle and frustrating is that with my CPU at rest circa 5% with no browsers or apps running.Then I play a movie in VLC or the default MoviePLayer my CPU jump 80% to 85 or 95% and the video becomes unwatchable.

Please help as I dont want to have to boot into XP just to watch a movie!!

Dell Inspiron 9300
Pentium M 1.73
2GB ram 1GB swap...
Karmic
Kernel 2.6.31-15

Thanks o wise ones:o

---

### Post by jonny_bowes on 2009-11-28
Bump:p

---

### Post by aaronchall on 2009-11-29
Jonny, I have the exact same setup as you.  I haven't done a whole lot with my laptop after this install, but I have run the following code, as per the multimedia instructions for my Ubuntu distribution:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

```I have just tested a DVD, which runs fine, and my CPU is running at about 74% capacity with it running and top of 33% when not.  However, I *have* set my CPU Frequency Scaling to 1.73 GHz, with a similarly named tool that I found when I right clicked the Gnome panel at the top (or bottom) of the screen and clicked "Add to panel..."  This setting gives me more responsiveness when I don't care too much about power consumption (that is, when I'm plugged in to the wall).  Maybe this is the problem?  Or do you have a more difficult video test?

Also, to everyone else out there with an Inspiron 9300, feel free to friend me, and maybe we can help each other with similar problems.

Aaron

---

