---
title: "Sound Converter does not work."
date: 2009-03-01
forum: Multimedia Software
---

### Post by missbliss on 2009-03-01
Sup all.  I've got Sound Converter so I can decode my flac files.  When I put the files in there to decode it says it decodes them after 2 seconds.  I then open up the directory in which they are saved and they are all there with as .mp3 files but with 0 bytes.



Anyone know what the deal is?


I have downloaded flac frontend but can't figure out how to use it in the terminal.  Suggestions on that?

---

### Post by mc4man on 2009-03-01
I don't have soundconverter on this install, probably you need gstreamer0.10-plugins-ugly, gstreamer0.10-ffmpeg, and libmp3lame0 (or liblame0 in hardy

What I'd probably do is use flac to decode to .wav and lame to encode to mp3.

You could do a batch convert with a simple script or even just one 'run on' command
(decode all the .flac's to same name .wav, encode the .wav's to same name .mp3 at whatever quality you want, delete the .wav's, and move the .flac's or .mp3's to where ever you want.

---

### Post by missbliss on 2009-03-02
> **mc4man said:**
> I don't have soundconverter on this install, probably you need gstreamer0.10-plugins-ugly, gstreamer0.10-ffmpeg, and libmp3lame0 (or liblame0 in hardy

What I'd probably do is use flac to decode to .wav and lame to encode to mp3.

You could do a batch convert with a simple script or even just one 'run on' command
(decode all the .flac's to same name .wav, encode the .wav's to same name .mp3 at whatever quality you want, delete the .wav's, and move the .flac's or .mp3's to where ever you want.

Do you know of a tutorial to help me with the flac script?  I have zero idea how to do this.  :-)

---

### Post by missbliss on 2009-03-02
Okay, I've come to figure out I must be missing something as far as the mp3 conversion goes b/c I got the bright idea to try and decode to wav and it worked fine.  I installed the packages you suggested but it didn't seem to help.  Possibly a reboot might do the trick though.

---

### Post by mc4man on 2009-03-02
I don't really use gstreamer apps that much, you could simply go 
```
sudo apt-get install ubuntu-restricted-extras
```
which will install all the plugins and a bunch more.
here's a thread that shows the useful plugins in a screenshot if you don't want the extra crap from above command (click 2 or 3 times on screenshot to magnify
[http://ubuntuforums.org/showthread.php?p=6797639#post6797639](http://ubuntuforums.org/showthread.php?p=6797639#post6797639)


As far as scripts or commands, very simple if you know how to cd to the folder containing the .flac's.

I'd install nautilus-open-terminal which allows you to right click on or in a folder and open a terminal at the correct prompt.

There's no advantage to using over soundconverter unless you want to control and use lame parameters that are unavailable in soundconverter.

For converting without passing the 'tags' a very simple command or script could be used.

To convert with the 'tags' a script is needed

I've got one for each, but no sense posting them unless your interested

---

