---
title: "Convert M4a to audio/mp3"
date: 2009-05-05
forum: Multimedia Software
---

### Post by foo-monger on 2009-05-05
Hi,

Does anyone know of any programs to convert my iTunes M4a songs to mp3 or audio cd?  

I cant seem to find anything thats free to do the job.

Cheers,

Foo.

---

### Post by logos34 on 2009-05-05
foobar2000 (on wine) is great. handles any format + tag info (need [foo_input_alac]("http://www.foobar2000.org/?page=Download") decoder plugin). Does everything, even cddb lookup, tagging, etc.  There's dBpoweramp too (wine again.  burner too)

ffmpeg and mplayer (terminal)

Here's two m4a to wav batch convert scripts:

[ATTACH]112561[/ATTACH]
[ATTACH]112562[/ATTACH]

[Edit]: Brasero can directly transcode m4a lossless and burn audiocd.  (must call ffmpeg or something.  I use k3b mostly, which can't read alac).

hope that helps

---

### Post by mc4man on 2009-05-05
For cd's any of the command line or scripts would be fine (m4a too .wav), then k3b can burn  to cd.

For mp3's it a matter of tags and or if you want more control of the the encoder (lame) options

Gui's such as soundconverter will 'transfer the tags and do an decent encoding job.
Soundkonverter has ways to use custom parameters and will also transfer tags (though soundkonverter's setting's seem to be a pita to set

I would think either could use itunes tags,

 I use abcde as a ripper with neroAacEnc doing the encoding and Atomicparsley the tagging and a quick look shows soundconverter re tagged exactly. (I believe Atomicparsley uses itunes style tags

When I have wma lossless, .wav's and m4a's that weren't tagged or I want to use certain lame parameters I use a script that converts and tags based on some interactive info and track name, number

---

