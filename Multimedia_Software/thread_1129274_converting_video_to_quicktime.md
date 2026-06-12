---
title: "converting video to quicktime"
date: 2009-04-18
forum: Multimedia Software
---

### Post by sneeks on 2009-04-18
hi,i use avidemux and winff for video conversion and editing,as i make some tutorial video's.
now the problem is that i cant get winff to convert to quicktime.
i seem to have all the codecs etc,but when my pc updates some of the updates,which winff is one,are greyed out and i can not select the package.
or do i need to go elsewhere and get them manually.

---

### Post by paul.gevers on 2009-04-19
> **sneeks said:**
> hi,i use avidemux and winff for video conversion and editing,as i make some tutorial video's.
now the problem is that i cant get winff to convert to quicktime.
i seem to have all the codecs etc,but when my pc updates some of the updates,which winff is one,are greyed out and i can not select the package.
or do i need to go elsewhere and get them manually.

Some trivial question that can help:
What error do you get if you try to convert to quicktime?
Did you use the quicktime preset of winff?

Are you still using Ubuntu 7.10 Gutsy Gibbon (as said in the information next to your post)? I don't know how you got winff to work then. So it would also help to know some more information.

What version of ubuntu are you running now?
How did you install winff?
What is the version number of winff now?
What program do you use to update your pc?

---

### Post by sneeks on 2009-04-19
> **paul.gevers said:**
> Some trivial question that can help:
What error do you get if you try to convert to quicktime?
Did you use the quicktime preset of winff?

Are you still using Ubuntu 7.10 Gutsy Gibbon (as said in the information next to your post)? I don't know how you got winff to work then. So it would also help to know some more information.

What version of ubuntu are you running now?
How did you install winff?
What is the version number of winff now?
What program do you use to update your pc?

the error message is acc not found,,still using 7.10 ,installed winff from repo's.
version is 0.42
and update manager for updates.

---

### Post by paul.gevers on 2009-04-20
> **sneeks said:**
> the error message is acc not found,,still using 7.10 ,installed winff from repo's.
version is 0.42
and update manager for updates.

The error is probably aac not found. Right? (Please copy/paste the full output next time, it is just easier because you also see the context). I bet you have some medibuntu repositories installed. Try using libaac instead of aac as the codec (newer versions of ffmpeg changed the api).

You can get up-to-date presets [here]("http://winff.googlecode.com/files/presets-libavcodec51-v4.xml.tar.gz") or [here]("http://winff.googlecode.com/files/presets-libavcodec52-v3.xml.tar.gz") depending on your version of libavcodec (either libavcodec51 or libavcodec52 or libavcodec-unstripped-51 or libavcodec-unstripped-52). Instructions on how to install a new version of the presets are on the [Winff wiki]("http://code.google.com/p/winff/wiki/InstallPresetsxml")

---

