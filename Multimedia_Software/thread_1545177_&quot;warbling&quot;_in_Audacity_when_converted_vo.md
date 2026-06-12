---
title: "&quot;warbling&quot; in Audacity when converted voice recording"
date: 2010-08-03
forum: Multimedia Software
---

### Post by CJ_Hudson on 2010-08-03
Hi,
I have been playing around with Audacity for a few weeks and found it a stupendous piece of software, except on a recent voice recording where the source file (.aup) is fine but when it converts it to MP3 there is some 'warbling' i.e. unwanted modulation on the voice.
How can this be? Surely the conversion process should not have this effect. Other recording I have converted sound fine.
Please, can anyone explain and/or does anyone have a fix?

---

### Post by ajgreeny on 2010-08-03
I can't imagine why that should happen, but just to try it out, save the file as a wav file, rather than mp3 then convert it to mp3 with something like winff if you want a gui, or ffmpeg in the command line.  I have never ever saved anything as an .aup so can not say whether that has any bearing on the problem, but wav to mp3 should work OK, using the alternatives I mentioned, or even using audacity if you prefer to try that.

---

### Post by CJ_Hudson on 2010-08-04
I think I know the reason. It was a slightly wobbly recording in the first place (from v. old cassette tape) and for some reason (i.e. sample rate) this just emphasised the 'wobblyness'. I thought of using other conversion software.
Thanks for your help.

---

