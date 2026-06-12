---
title: "Need a scripting enabled WAVe editor or a command line tool for cutting WAVEs"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by swarog on 2007-11-27
I have a long WAVE file with some speech and I want to extract from that file things I am interested in and filter out everything else, and then write down the chosen fragments each into separate file. I have been using GNUsound to listen and determine fragments time ranges, so I have composed a text file with time ranges written in the first column and in the second one I have file names into which I want to write each fragment. 

But I really hate all that GUI stuff when it comes to copy/paste, drag'n'drop, file->save and all that kinds of things. It is so annoying for me. I even couldn't have managed to do it in GNUsound. I can not overwrite default setting for sampling rate for a newly created file there (I need 11025kHz and it shows me 44100 no matter of what I have set in Edit->Properties dialog.

So what I need is a sound editor with scripting capabilities or a tool to which I can just tell something like "cut -f T1 -t T2 source.wav -o output.wav" and it would do the job. Then I can just write a simple bash script to scan my file with ranges and accomplish the whole task. Is there such a tool?

---

### Post by disturbed1 on 2007-11-27
Sox will do what your want.

---

### Post by swarog on 2007-11-29
Thank you, disturbed1!

Sox with  *trim* effect is just what I need :)

---

