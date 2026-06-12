---
title: "24 bit sound problems with mythmusic"
date: 2010-06-20
forum: Mythbuntu
---

### Post by Erkander on 2010-06-20
Sigh.  Just when I thought I had everything fixed.

I've got several pieces of music in 24 bit wav and flac.  On my old Knoppmyth install the wav's would play but not the flacs.

On my brand new Mythbuntu box, the flacs and wavs both make the same sound.  Horrible static in the Left speaker, and some music (can't really tell what exactly though) through the other.

I'm using a coax spdif to a tuner that can handle anything pretty much.

Please Help.  This was one of the things I loved most about my system.

EDIT: BTW, VLC from the desktop can play both the wavs and the flacs just fine.

Thanks in advance.

--Erkander

---

### Post by joho500 on 2010-06-22
Did you install the codecs from Mythbuntu Control Center? I'm not using 10.04 so I don't know were they are located in that version of MCC.

Joost

---

### Post by Erkander on 2010-06-24
Does anybody know what exactly I need to download and where that would be?  Sorry, still very Newbish.

--Erkander

---

### Post by jyavenard on 2010-06-24
> **Erkander said:**
> Does anybody know what exactly I need to download and where that would be?  Sorry, still very Newbish.

--Erkander

There is no 24 bits audio support in MythTV in 0.23...

A hack was added for video playback that downconvert 24 bits (as used by E-AC3) to 16 bits (changeset 22608  )... Note that the down-conversion is less than ideal

This hack wasn't applied to mythmusic.
I made a patch however available at [http://svn.mythtv.org/trac/ticket/7410](http://svn.mythtv.org/trac/ticket/7410) ; the trunk patch should apply on 0.23

This other possibility is to upgrade to the current 0.24 (trunk) ; mythtv has now full support of > 16 bits audio ..
This is my recommended solution.. audio will be far better in 0.24

---

### Post by Erkander on 2010-06-25
Thanks for the advice!  I have gotten MPD working and have been using it to play music.  I like it better than MythMusic anyways and it'll play anything.  I'll probably just wait until .24 is finalized and upgrade then.

--Erkander

---

