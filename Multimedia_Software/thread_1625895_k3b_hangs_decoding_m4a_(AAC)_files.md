---
title: "k3b hangs decoding m4a (AAC) files"
date: 2010-11-19
forum: Multimedia Software
---

### Post by meow9th on 2010-11-19
I'm trying to burn a k3b project with mp3s and m4as to an audio CD. K3b decodes the mp3s in mere seconds, but appears to hang when trying to decode the m4as (AAC) - I cancelled after 5 minutes of absolutely zero progress on the first m4a it hit.[PHP][/PHP]

I tried searching for k3b/AAC decoding issues, but almost everything I found was a few years old, which I assume means that k3b supports AAC decoding out of the box now? I can play the m4as in Amarok without a hitch, so I assume I have the packages to decode installed fine.

Does anyone have any ideas on what's wrong? If I can't get k3b to burn my m4as directly, I'll use soundKonverter or somesuch to convert to a different format. But skipping that extra step would be ideal. Thanks for the help.

EDIT:
I found out two things that kind of resolve my issue.

**k3b bug**
When I ran k3b from terminal, I saw the following error message when k3b tried to decode the m4as:
```
[aac @ 0x7f8cb058c290]buffer smaller than AVCODEC_MAX_AUDIO_FRAME_SIZE
```
When I searched on this, I found a [bug report]("https://bugs.kde.org/show_bug.cgi?id=182595"). I guess the bug has been fixed and one day we'll get it in an update.

**AAC decoder**
At this point I decided to give up and just convert my m4as with soundKonverter. But I found that soundKonverter also hung when trying to decode my m4as! When I searched on this problem, I found that [the fix]("https://answers.launchpad.net/ubuntu/+source/soundkonverter/+question/60904") was to change the m4a decoder to 'mplayer'. I believe the default was faad.

---

