---
title: "How to open/convert ZVR files"
date: 2009-03-29
forum: Multimedia Software
---

### Post by Canaryguy on 2009-03-29
Hello,

     I have a voice recorder and it gives me the audio files in ZVR format. Is there any way I can convert that format to WAV or MP3?

Thanks.

---

### Post by irtysh on 2009-04-03
I don't know if there's any native linux application for this. But the VoiceTracer program by Philips works well under Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7757](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7757)
it can be downloaded here:
[http://www.dictation.philips.com/index.php?id=70&no_cache=1&file=VoiceTracer_v3.7.0.4.zip&uid=1358#lic-code](http://www.dictation.philips.com/index.php?id=70&no_cache=1&file=VoiceTracer_v3.7.0.4.zip&uid=1358#lic-code)

---

### Post by FakeOutdoorsman on 2009-04-03
Can you make a small zvr sample available?

---

### Post by Canaryguy on 2009-04-10
Thanks for your help irtysh.

A zvr file sample can be found here:
[http://www.mediafire.com/?sharekey=31781903eef0a2bf8c9e7c56ba37815fa364d08a2bcf6c06](http://www.mediafire.com/?sharekey=31781903eef0a2bf8c9e7c56ba37815fa364d08a2bcf6c06)

---

### Post by FakeOutdoorsman on 2009-04-10
I thought it was worth a try, but I was unable to get FFmpeg, MPlayer, or mediainfo to even recognize this format.

---

### Post by mc4man on 2009-04-10
You can try this prog under wine (download from the mirror site
[http://www.free-codecs.com/ZVR_Converter_download.htm](http://www.free-codecs.com/ZVR_Converter_download.htm)

It works on some zvr files, actually did on your sample, 50 secs of Beethoven's fifth I believe.

The resulting .wav had an odd 'displayed' play time in amarok (27 hrs.), running thru sox fixed the header

> doug@doug-desktop:~$ sox IC_A0001.wav testz.wav


If you try and it won't open in wine then pm me and I'll upload a custom system32 that you can merge into the default one (has some useful dll's

---

### Post by obi_juan_ on 2011-01-21
Thanks! Works like a charm!!

---

