---
title: "E: Package sun-java6-fonts has no installation candidate"
date: 2010-08-03
forum: Multimedia Software
---

### Post by zander1013 on 2010-08-03
hi,
i get this error at the second step of 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) for 32-bit ubuntu users...

> oem@oem-laptop:~$ sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-fonts has no installation candidate
oem@oem-laptop:~$ 

it is a fresh install of 10.04 on a gateway t-series laptop. otherwise all seems to be in order.

please advise.

---

### Post by kerry_s on 2010-08-03
sun java is in the other software-> partner repo.

---

### Post by zander1013 on 2010-08-03
> **kerry_s said:**
> sun java is in the other software-> partner repo.

hi,

okay i have checked "http://archive.canonical.com/ubuntu karmic partner" in software sources>other software tab and then closed it. i ran "sudo apt-get update" 2x but still got the same error when i tried to run the second step.

so i backed up ran the first step "quick method" and then the second step as above but i am still getting 

> oem@oem-laptop:~$ sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-fonts has no installation candidate
oem@oem-laptop:~$ 

when i open software sources>other software the "partners" row is still checked in addition to the medibuntu repository.

can you advise farther please?

thank you:confused:

---

### Post by kerry_s on 2010-08-04
first your doing it the hard way.

all those things your installing comes in "ubuntu-restricted-extras", so you only need to install that. that will install the open source java, so you'll still have to install sun if you want, but firefox is set to use open java anyways. i have sun cause i use chromium, which doesn't work with open java.

use synaptic to check for sun java.

ps: why are you using karmic(9.10) instead of lucid(10.04)?

---

### Post by zander1013 on 2010-08-04
ty kerry_s,

i had installed 9.10 first because it offered an oem install option. i have worked around the problem by changing Software Sources>Other Software>[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) to "lucid" in the Distribution field using the Edit feature in the Software Sources dialog after selecting the "partner" repository as previously advised.

perhaps this was some artifact from the upgrade that was not handled properly?

thank you for your help.

---

### Post by kerry_s on 2010-08-04
i think they all offer a oem install, for 10.04 just hit any key at boot & i think it's in the f6 or f7 option.

---

