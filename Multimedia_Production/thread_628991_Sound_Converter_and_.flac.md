---
title: "Sound Converter and .flac"
date: 2007-12-01
forum: Multimedia Production
---

### Post by bruban on 2007-12-01
I'm trying to use 'Sound Converter' to convert a CD into .flac format files.

I'm using Ubuntu 7.10 with restricted formats installed.


When I try to extract (backup) my CD into .flac format files, I get the error message:

> Sound Juicer could not extract this CD.
Reason: File not found


This is a clean install of Ubuntu 7.10.

I was able to do this OK with Ubuntu 7.04.

Any ideas?

---

### Post by logos34 on 2007-12-02
You don't need to use soundconverter--you should be able to rip the cd straight to flac format using sound-juicer.

It will only rip CD-audio (CDDA)--if this is an mp3 disc it won't work.  

If you installed the ubuntu-restricted-extras metapackage, that should have dragged in gstreamer base, good and whatnot, which contain ogg, flac and the rest.  You;ve obviously read the restricted formats page, so not sure what else to suggest.  It's able to access the cdrom drive, so that's not the issue.

---

### Post by bruban on 2007-12-03
Thanks for your reply.

I've just realised that I was trying to use sound-juicer, not sound converter as my original post stated.

Sorry for the conversion.

I have retried this but still have the same problem.

Has anyone been able to successfully cut an audio CD to FLAC format using sound-juicer on Ubuntu 7.10?

If so, did you do anything special?

---

