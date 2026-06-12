---
title: "Random DVD playback failures in 8.04"
date: 2009-05-04
forum: Multimedia Software
---

### Post by pauna on 2009-05-04
I have been running Hardy Heron 8.04 based Mythbuntu box as our HTPC for a year now, but now the machine has started to exhibit odd playback problems on DVD movies.

To keep it short, some DVDs play and some don't, the error message is from libdvdread saying "Can't open /dev/dvd for reading". Key problem features are
[LIST]
[*]It's not disk specific (DVD that did not play yesterday might play today and vice versa)
[*]It's not just a Disney copy protection issue, yesterday the Little Mermaid played nicely, now it doesn't.
[*]The DVD unit is not broken (tested with a brand new unit and the problem did not go away)
[*]The IDE bus isn't fried. The new DVD unit was a SATA player and it didn't work any better. The DVD is the only IDE device, the disk is SATA.
[*]It's not a MythTV problem (if MythTV and its xine can't play the disk, lsdvd can't read the DVD either)
[*]Reboot does not always fix the problem. Sometimes yes, sometimes no.
[/LIST]

Ubuntu and MythTV have all the latest patches installed, MythTV is using weekly . This is a problem that started a month or so ago. Otherwise the box seems to function nicely.

Any hints on things I could try to debug further?

---

