---
title: "how do I batch-resample WAV files?"
date: 2010-10-21
forum: Multimedia Software
---

### Post by potiphera on 2010-10-21
I have a set of WAV files with a 48 kHz sample rate (and some other sets in higher sample rates), and I want to resample them to 44.1 kHz.  I usually use Audacity, but there's no resample option in "edit chains," and I don't want to resample the files manually one at a time.  I tried soundconverter, which works great for converting between formats, but it gave me files that were too large and were unusable due to bad headers.  Are there any programs that will do this correctly?  I prefer graphical interfaces, but I'm fine with command line programs as long as they can convert the files en masse.  I'm on Ubuntu Studio 10.04.  Thanks!

---

### Post by ron999 on 2010-10-21
Hi
**WinFF** has a preset 'Wav for CD'.
That will resample to 44.1 KHz.
It might be in the Ubuntu repo now.
Otherwise visit the website and use the PPA.
Here:-[http://winff.org/html_new/]("http://winff.org/html_new/")

---

### Post by potiphera on 2010-10-22
Thanks, WinFF works great!

---

