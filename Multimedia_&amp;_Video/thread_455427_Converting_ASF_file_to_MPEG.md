---
title: "Converting ASF file to MPEG"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by Woody_in_MN on 2007-05-26
My digital movie camera (AIPTEK) records movies as ASF files.  Can someone suggest a program to convert these ASF files to MPEG, or MOV file format?  I have not had much luck trying this with VLC.  VLC converts the video OK in some formats - but it is not converting the audio.  Or atleast not converting audio in a format that I can play bak with VLC, or Totem.

Thanks in advance,

 - w

---

### Post by Judo on 2007-05-26
Are you looking for something with a graphical interface?  If you're not afraid of command line, I could give you some commands for MEncoder.

---

### Post by Woody_in_MN on 2007-05-26
Judo,

I was hoping for something graphical, but if you do not know of any I guess I could try the commands.

 Thanks,

 - w

---

### Post by Judo on 2007-05-26
I've used some graphical ones before and never really liked them.  They seem too complicated compared to command line.

```
mencoder inputmovie.asf -ovc xvid -xvidencopts chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:bitrate=4000 -oac mp3lame -lameopts abr:br=192 -o outputmovie.avi
```

I think I got that right.  If the detail is low, you can increase the bitrate (bitrate=3000) to something higher.  I'm not sure about your camera;s aspect ratio so I left out the scaling, but I could still help you with that if needed.

---

### Post by pelicanghost on 2007-06-23
I typed that in, and I got this:


Compiled with runtime CPU detection.
File not found: 'inputmovie.asf'
Failed to open inputmovie.asf.
Cannot open file/device.
  
Any tips?

---

### Post by dennus on 2007-07-07
```
mencoder inputmovie.asf -ovc xvid -xvidencopts chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:bitrate=4000 -oac mp3lame -lameopts abr:br=192 -o outputmovie.avi
```

Hi!

I've have tried your suggestion on my clip.asf, downloaded from the internet, but I get the following message...
----
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
-----

Do you have any idea what the problem could be?

Dennis

---

