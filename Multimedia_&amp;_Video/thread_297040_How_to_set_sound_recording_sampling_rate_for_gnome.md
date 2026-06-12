---
title: "How to set sound recording sampling rate for gnome applications"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by casaschi on 2006-11-10
I'm using Edgy, fresh from booting on live CD system.

The issue I have is with properly recording sound with gnome applications.

If I try recording sounds using a gnome application (like thee sound recorder from the Applications->Sound&Video menu, or skype) then the recorded sound quality is very very bad, choppy metallic sound with noise and echo.
If I save the file with the sound recorder as .wav file and then I try playing it back with aplay, I get following output:

[I]ubuntu@ubuntu:~$ aplay gsr-record-Untitled-6432.wav 
Playing WAVE 'gsr-record-Untitled-6432.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Mono[/I]

If I try instead of recording the sound with arecord, then the sound is recorded perfectly! On the console I get the following output:

[I]ubuntu@ubuntu:~$ arecord t.wav
Recording WAVE 't.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono
Aborted by signal Interrupt...
ubuntu@ubuntu:~$ aplay t.wav 
Playing WAVE 't.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono[/I]

So, the difference that appears immediately is on the "Signed 16 bit Little Endian" vs "Unsigned 8 bit" and the sampling rate.

How should I configure Ubuntu Edgy so that the settings used by gnome applications such as the sound recorder are the same as used by aplay ???

Any other reccomendation welcome of course.

Thanks in advance!

-- Paolo

---

### Post by ahaslam on 2006-11-10
I ran gnome-audio-profiles-properties and created a new profile with the following values:

Profile name: CD Quality, Lossy
Profile Description: Test
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
File Extension: mp3

That should record in VBR, if you wush to specify a bit rate add something like this: bitrate=192

That profile should then be available in any recording/ripping package.

For further info check out these sites:
[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)
[http://ubuntuforums.org/showthread.php?t=189140&highlight=rip+mp3](http://ubuntuforums.org/showthread.php?t=189140&highlight=rip+mp3)

Tony.

---

### Post by casaschi on 2006-11-11
That does not really help me.

I think there might be a problem with the soundcard setting, so resampling does not help.

Also, some applications like skype dont give you any options to choose from.

So my question remains how to set the sampling rate in my soundcard (ESS Maestro ES1978) to a new default value.

---

