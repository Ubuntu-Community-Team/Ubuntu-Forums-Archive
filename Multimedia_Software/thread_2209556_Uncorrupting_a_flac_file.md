---
title: "Uncorrupting a flac file"
date: 2014-03-06
forum: Multimedia Software
---

### Post by Lars Noodén on 2014-03-06
I have a FLAC file that won't play through to the end.  It gets part way in and then the player makes a pop and then stops playing.  How do I check the file for corruption and fix it if it is corrupted?

---

### Post by bapoumba on 2014-03-06
May be have a look here : [http://comments.gmane.org/gmane.comp.audio.compression.flac.user/1684](http://comments.gmane.org/gmane.comp.audio.compression.flac.user/1684) ?
Couple commands that could lead you to point out the origin of the error.

---

### Post by Lars Noodén on 2014-03-06
Thanks. I'll have to look at the *flac* tool more closely.  Unfortunately neither the good files nor the bad ones have MD5sums embedded.

```

$ flac -aF 9\ -\ I\'ll\ Be\ Your\ Mirror.flac 

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

9 - I'll Be Your Mirror.flac: WARNING, cannot check MD5 signature since it was unset in the STREAMINFO
done    

```

---

### Post by Lars Noodén on 2014-03-06
There may be a bug with sound-juicer.  I ended up re-ripping the track and still got the same error.  However, when ripping to ogg, it played fine.  Then I used audacity to convert to flac (probably lost some quality there in the initial rip) and that made a proper MD5 checksum.

---

### Post by bapoumba on 2014-03-06
> **Lars Noodén said:**
> There may be a bug with sound-juicer.  I ended up re-ripping the track and still got the same error.  However, when ripping to ogg, it played fine.  Then I used audacity to convert to flac (probably lost some quality there in the initial rip) and that made a proper MD5 checksum.

Ah, have you tried to start it from the command line and see if there are any useful errors to look at ?

---

### Post by SuperFreak on 2014-03-06
[http://www.softpedia.com/get/Multimedia/Audio/Other-AUDIO-Tools/AudioTester.shtml]("http://www.softpedia.com/get/Multimedia/Audio/Other-AUDIO-Tools/AudioTester.shtml")

I have used this in WINE

---

### Post by Lars Noodén on 2014-03-07
> **bapoumba said:**
> Ah, have you tried to start it from the command line and see if there are any useful errors to look at ?

There are errors, but I'm not sure about useful ones.  These repeat a lot with the disc in.

```

Unrecognised track attribute: 'id'
...
Unrecognised work element: 'iswc'
...
Unrecognised relation attribute: 'type-id'

```

These came when ripping:

```

Unrecognised relation attribute: 'type-id'
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

** (sound-juicer:22024): WARNING **: Problem calling inhibit GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (sound-juicer:22024): WARNING **: Invalid cookie

```

---

### Post by bapoumba on 2014-03-07
Are you trying to read the file from a CD ? Some of the errors pop up old bugs.

---

### Post by Lars Noodén on 2014-03-08
I was reading from HD intially but decided to try re-ripping with sound-juicer.  

If I rip directly to flac, I get the same problem again including lack of checksum in the metadata.  If I go via ogg and then convert with Audacity to flac, I do not get a broken file and get a proper MD5 checksum in the metadata.  If I just copy the wav file from the CD, it plays through unbroken.  I'm using Clementine for the player if that matters.

---

### Post by bapoumba on 2014-03-08
I see you reported a bug. let's hope someone has a look at it.
[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/1288872](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/1288872)

May be have a look here, even though it is for an older release ?
[http://ubuntuforums.org/showthread.php?t=1776443](http://ubuntuforums.org/showthread.php?t=1776443)

---

