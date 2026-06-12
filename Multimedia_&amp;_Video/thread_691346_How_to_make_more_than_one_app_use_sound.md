---
title: "How to make more than one app use sound?"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by SilverTL on 2008-02-08
Mabey this is answered elsewhere but I couldn't find it, I've never much cared to figure this out in the past but I seem to be using linux more and more these days.  Anyway my problem is that only one App can use the sound at a time, and what I want to be able to do is play music while playing games without losing out on sound on either one of these programs.  I figure it's just a matter of making a mixer work correctly so if there is a general guide for this please point me to it.
Thanks.

---

### Post by Crank-N-Jam on 2008-02-08
I'm a newb, but I have noticed this (rather annoying at times) issue as well.

From what I can tell, my experience seems to point to software using different audio controls, ie Jack vs. ALSA.  In other words, if all the programs I have open all use Jack, I have no problems.  But lets say I launch Amarok which I have using ALSA it won't have any sound.

I may be completely off track and I don't know if there is a solution (except maybe using audio software that uses the same controls).  My gut tells me that since one or the other has the card locked, there isn't much you can do (but again, I'm a Linux newb and probably don't know what I'm talking about).  :)

Jason

---

### Post by linuxwizard on 2008-02-08
Look on this page for > Getting more than one application to use the soundcard at the same time > [https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705](https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705)

---

### Post by SilverTL on 2008-02-08
> **linuxwizard said:**
> Look on this page for > Getting more than one application to use the soundcard at the same time > [https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705](https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705)

I looked at that already but it seems to be telling me to tell my programs to use different mixers which seems to be not quite what I would like to do.  I'll try it anyway mabey I understood that wrong as I was looking at this when i first woke up.  In either case this should be interesting to use with Cedega/wine.


EDIT: Didn't work.

---

