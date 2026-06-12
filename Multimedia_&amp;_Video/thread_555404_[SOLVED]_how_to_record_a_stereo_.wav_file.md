---
title: "[SOLVED] how to record a stereo .wav file?"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-09-20
How to record a stereo .wav file? I'm using audacity to export a recording as a .wav file for use in Kino as a dubbing track. But the track plays double speed in Kino (it plays regular speed everywhere else). I've searched the Kino forum, and there was one posting describing a predicament similar to mine. The solution was not to use a mono .wav file, but rather a stereo .wav file.

---

### Post by alterpinguin on 2007-09-20
man arecord
read to example recording cd-quality wav
and for convertion, there are a lot of tools .. maybe the most famous is sox, read its doc too.

---

### Post by berliita on 2007-09-21
Thanks, alterpinguin. Your conversion solution worked for me.

Here's the template of the command line i used to do the conversion from an ".ogg" file, recorded in Audacity with the default parameters, to a stereo ".wav" file, as required by Kino:
<code>
$ sox input.ogg -c 2 output.wav
</code>

The "c" option indicates that the output should be stereo. To quote the sox manpage:
<quote>
 -c channels
The  number  of sound channels in the data file.  This may be 1, 2, or 4; for mono, stereo, or quad sound data.   To  cause the  output  file to have a different number of channels than the input file, include this  option  with  the  output  file options.
</quote>

Here's a simplified template of the sox command:
<code>
sox [input-options] input-file [output-options] output-file
</code>

---

