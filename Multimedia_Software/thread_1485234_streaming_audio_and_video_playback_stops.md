---
title: "streaming audio and video playback stops"
date: 2010-05-16
forum: Multimedia Software
---

### Post by linuxnoob40 on 2010-05-16
ok i upgraded to 10.04 lucid and now if i want to stream audio i get jerky audio with screen flickers and video streaming or not causes a complete lockup of the application. this all worked fine with 9.10. any ideas ?

---

### Post by gnik1 on 2010-05-16
Is this through firefox, while browsing?

---

### Post by linuxnoob40 on 2010-05-16
sometimes yes but even movies i have saved to my desktop will not play and will lock up and just for s&gs i used chrome to see if it was Firefox and it does the same

---

### Post by gnik1 on 2010-05-16
Since it's a fresh install. I'd check for updated drivers via
System > Administration > Hardware Drivers

maybe you're video isn't set to the recommended driver. I know I had to switch to that option for my video before it improved and let me use desktop effects

---

### Post by linuxnoob40 on 2010-05-16
not a fresh install its an upgraded install from 9.10

---

### Post by lidex on 2010-05-16
Go to this page:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
Do parts 1 and 2. At least read through the rest - it's good info.

---

### Post by linuxnoob40 on 2010-05-16
i have done all the perperation from this but when it comes to installation i get nothing but
> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding libboost-thread1.40.0 libboost-date-time1.40.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
libmp3lame0 is already the newest version.
libmp3lame0 set to manually installed.
Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-fonts has no installation candidate


i am at a loss of what to do here

---

### Post by lidex on 2010-05-16
Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

And this one as well:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by linuxnoob40 on 2010-05-17
ok well i cant do this either what i get is as follows

>  mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
cp: cannot stat `/home/steven/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory


what to do from here?

---

### Post by lidex on 2010-05-17
> **linuxnoob40 said:**
> ok well i cant do this either what i get is as follows
what to do from here?
That's not unusual.
Follow the other link, do what it says, then reboot.

---

### Post by linuxnoob40 on 2010-05-17
hate to sound stupid but it asks what application to use to open it ?

---

### Post by linuxnoob40 on 2010-05-17
ok that seems to have fixed movies i have on my harddrive but any streaming movies or streaming audio just halts to a complete stop


guess i spoke too soon

---

### Post by linuxnoob40 on 2010-05-18
i have narowed this down to a sound issue as everything seems to fixed on the video side but sound is kinda messed up and it will just quit and i have to reboot to get my sound back

---

