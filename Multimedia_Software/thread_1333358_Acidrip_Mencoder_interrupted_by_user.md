---
title: "Acidrip: Mencoder interrupted by user"
date: 2009-11-21
forum: Multimedia Software
---

### Post by trayzz on 2009-11-21
i searched through some feeds already but couldn't find an answer. 

Acidrip produces a file but stops right after with the error message "mencoder interrupted by user". I checked the debug

```
No matching DVD audio language found!
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
```does anybody know which library demuxer is included in?

---

### Post by shields on 2010-02-04
Ever get a solution on this?

Thanks.

---

### Post by Zlobomir on 2010-03-02
Check the Debug, most probably you miss a codec. In my case it was the sound, since smo said that lamemp3 was not making synced audio. However in my case I switched to lamemp3 and it was fine. You have to install it, but the audio player does so usually on a fresh system. This is not my solution, kinda reposting.

Zlobi

---

### Post by BigMeanMikeRich on 2010-07-19
For me, the issue was that my system did not have libdvdcss installed.  If you follow the [instructions here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") they will help you install this library (which requires libdvdread4 -- install this from synaptic, or you won't be able to read any dvds in the first place).

To quote the Ubuntu help article linked to above,

> Most commercial DVDs are encrypted with CSS (the Content Scrambling System), which attempts to restrict the software that can play a DVD.

By installing the libdvdcss2 package you can play encrypted DVDs

This fixed my problems with Acidrip, k9copy and dvd95.  Hooray for debugging output! :D

---

### Post by Linuxforall on 2010-07-20
Also add RVM's ppa for newer mplayer mencoder than the one included.

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

