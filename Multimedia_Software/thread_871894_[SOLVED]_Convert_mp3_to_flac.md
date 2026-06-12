---
title: "[SOLVED] Convert mp3 to flac?"
date: 2008-07-27
forum: Multimedia Software
---

### Post by NovaAesa on 2008-07-27
Hi, I'm wanting to convert a heap of mp3 files to flac files (don't ask, long story). I know there are a few ways of doing this with a GUI, but I have hundreds of files and am hoping to do it with a script so that I don't have to do lots and lots of clicking. So a CLI app or command would be good.

Does anyone know of such a thing? Thank you,

-Nova

---

### Post by forger on 2008-07-27
hm... converting from terminal can be a real pain, you'll have to save temporarily the ID3 tags :(
The soundconverter GUI application can load directories that contain audio files, it loads ID3 info automatically. It doesn't take much clicking :) It's in the Ubuntu repositories


You'll also need several other packages (codecs) in order to use it to convert mp3 to flac, give me a couple of minutes if I manage to find my usb stick with the info
Edit: can't find it, sorry!

---

### Post by forger on 2008-07-27
On the other hand, this blog post might help, using sox and a couple of other utilities:
[http://www.oreillynet.com/onlamp/blog/2004/11/convert_audio_between_mp3_flac.html](http://www.oreillynet.com/onlamp/blog/2004/11/convert_audio_between_mp3_flac.html)
[http://www.linuxforums.org/applications/sox__the_commandline_audio_workstation.html](http://www.linuxforums.org/applications/sox__the_commandline_audio_workstation.html)

---

### Post by NovaAesa on 2008-07-27
Thank you for those!

---

### Post by cozmicharlie on 2008-07-28
> **NovaAesa said:**
> Hi, I'm wanting to convert a heap of mp3 files to flac files (don't ask, long story). I know there are a few ways of doing this with a GUI, but I have hundreds of files and am hoping to do it with a script so that I don't have to do lots and lots of clicking. So a CLI app or command would be good.

Does anyone know of such a thing? Thank you,

-Nova

OK - I won't ask.  I will assume by your statement you know that converting from a lossy to lossless format is not a good idea - I will leave it at that.

I know this is marked solved but I would recommend PACPL ([http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl)).  It is command line and should be just what you are looking for.

Enjoy

---

### Post by NovaAesa on 2008-07-28
PACPL looks even better. I'll experiment with that one as well =] Thanks.

And yes, I know all about the perils of lossy to lossless :P

---

### Post by DPic on 2009-02-17
I too need to convert mp3 to FLAC. Jamendo.com only accepts FLAC or wav, etc, but the only copy i have in in mp3. When i used sound converter, Jamendo.com rejected the files for some reason. When i tried their desktop tool, it said that the files needed to be in 16 bit rate. When i looked at the file properties, next to bitrate is said "n/a". So, i'm assuming this is the problem. Anyone know how i can specify the bitrate?

---

### Post by DPic on 2009-02-18
Sorry, the error was actually  calling for "bit depth" not rate

---

