---
title: "sound card worked... now undetected"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by mentalis on 2008-02-18
my sound card onboard ( Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller according to lspci ) was detected and worked perfectly when i originally installed ( 7.10 ).  however, i rarely use sound and have since either upgraded :) or uninstalled, etc. some package to make it stop working. i'm not even sure how long it's been broken. aplay -l now says "no soundcards found". how do i get ubuntu to redetect it the way it did during install or otherwise diagnose this?  all my previous admin experience is on redhat or fedora. thanks

---

### Post by roadrocket13 on 2008-02-18
i've been dealing with a similar problem. mine's ICH6 though i believe the relevant module driver is still "snd-hda-intel"

here are some sites that may be of use....

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel")

EDIT:

try this one also [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

