---
title: "No sound through ALSA only OSS?"
date: 2009-01-13
forum: Multimedia Software
---

### Post by Sigma47 on 2009-01-13
Hello and thanks for taking the time to read this post. I installed Ubuntu Intrepid 64 this wknd after 2 years of contemplation and so far I have spent about 24 hrs getting everything set up to my liking and learning about Linux and its a great... so far... I am however having audio issues...

I have 2 sound cards: onboard is Realtek ALC880 and PCI is Cmedia I8738. I choose to use the PCI b/c the onboard has interference I believe is caused by the Network adapter... So anyway I am only getting sound through the XXXX (OSS) options in System>Preferences>sound. I have tried a myriad of hodge podge fixes and have failed to get any to work with the XXXXX (ALSA) options. When I open the alsamixer it shows pulseaudio as my default playback. And I have reinstalled alsa a few times to no avail. I added a line to the bottom of alsa-base canf so that it defaults to the PCI card for sound and thats about all that I know I've modified.

In my limited and short experience with the other problems I have solved here I think I have a config wrong and I probably only need to switch a line or something.

Much thanks for your time,

---

### Post by 2hot6ft2 on 2009-01-13
8.10 uses PulseAudio. Also there is a known bug in 8.10 that sets the sound to 0. See the first link below.
Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
A short version here. I suspect it will be modified.
[http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html)

There are more but this gives you some alternatives that are being used.

---

### Post by Sigma47 on 2009-01-13
2hot6ft2, thanks a bunch for the help the first link by psyke83 fixed the issue... You rock!!! This  community rocks!!! Ubuntu rocks!!! Stoked to be free of the MS shackles!!!

---

