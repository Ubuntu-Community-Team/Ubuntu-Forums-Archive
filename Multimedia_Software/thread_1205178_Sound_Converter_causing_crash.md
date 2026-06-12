---
title: "Sound Converter causing crash"
date: 2009-07-05
forum: Multimedia Software
---

### Post by BrynC on 2009-07-05
Running Jaunty, attempting to convert all my .wma to mp3/ogg files, using Sound Converter. I put in the files, tell it to convert, and computer shuts down after about 30secs.

Computer is an Acer Aspire 5535, standard hardware (Turion 2.1GHz processor, 3GB DDR2 RAM, 250GB HDD). Any hints on troubleshooting / fixing / other/better converters?

---

### Post by kassoulet on 2009-07-06
> **BrynC said:**
> Running Jaunty, attempting to convert all my .wma to mp3/ogg files, using Sound Converter. I put in the files, tell it to convert, and computer shuts down after about 30secs.

Computer is an Acer Aspire 5535, standard hardware (Turion 2.1GHz processor, 3GB DDR2 RAM, 250GB HDD). Any hints on troubleshooting / fixing / other/better converters?

Can you run in a console:
  ```
soundconverter --debug
```
Retry the conversion, and paste here the result?

---

### Post by BrynC on 2009-07-06
Been attempting to, sadly, it shuts down too quickly for me to grab everything out and paste it. It goes to the shutdown screen in fractions of a second, which isn't too useful.

Seems to only be occurring on bulk conversions though...

Bulk conversions - i.e. 30+ files

---

### Post by kassoulet on 2009-07-06
Try this instead:

```
soundconverter --debug > crash.log 2>&1
```

And paste here the crash.log file.
That's so amazing we managed to stop a computer by converting files :)

I fact It's maybe related to an overheating ?

---

### Post by 7sOQ5k on 2010-07-10
I'm finding this happening on 10.04 when converting a dozen TED talk mp4s to mp3. The computer shuts down after about 6 conversions. 

Details -
Linux ubuntu-3 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

The crash.log header starts with

SoundConverter 1.4.4
  using Gstreamer version: 0.10.28, Python binding version: 0.10.18
  using gio
  'faac' element not found, disabling AAC.
  using 3 thread(s)
...

Last lines are

got file duration: 467
got file duration: 1315
TagReading done...
TagReading done...
pipeline already stopped!
launching: 'giosrc location="file:///home/user/gpodder-downloads/TEDTalks%20(
video)/HillelCooperman_2010U.mp4" name=src ! decode

---

