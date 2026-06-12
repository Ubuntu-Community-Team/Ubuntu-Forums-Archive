---
title: "Batch convert audio in Video files"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Zack McCool on 2010-05-08
All right...   Here's the problem:

I use MythBuntu to watch movies on my television.  BUT, my Myth box is connected to the 5.1 audio receiver via a digital connection.  So, if a movie is encoded with AC3 in 6 channel audio, what I get out is all of the sounds except for voices, which in 5.1 would be sent to the center channel.

What I usually do is fire up avidemux and convert the audio to mp3 stereo, as converting to a 5.1 format usually ends up with a very odd sound (like running everything through an echo chamber).

What I'd like to do is run a script to batch-convert these files from AC3 to MP3.  

The video format may vary, but they are usually XVID.  

I am comfortable at the command line, but I am not well-versed in audio/video tool terms.  I don't need anything extravagant, I just want something that works.  Heck, even if it is done one at a time, having a shell script that I can use to simply type:

tool.sh inputfile.avi outputfile.avi

Would be great.

Anyone have a simple solution?

Thanks!
Joe

---

### Post by ron999 on 2010-05-08
> **Zack McCool said:**
> 

Anyone have a simple solution?

Thanks!
Joe

Hi
WinFF will batch create mp3 files from those video files.
It's here:-[http://winff.org/html_new/]("http://winff.org/html_new/")

---

### Post by Zack McCool on 2010-05-09
> **ron999 said:**
> Hi
WinFF will batch create mp3 files from those video files.
It's here:-[http://winff.org/html_new/]("http://winff.org/html_new/")

I just installed it, and you're right, it will create MP3's, if I so desire, but what I am looking to do is create the same XVID AVI with MP3 instead of AC3 audio tracks.

I don't see an option for that in there, but if you can give me the right clue, perhaps it will do the job.  I do like the interface...

---

### Post by ron999 on 2010-05-09
My bad, I didn't understand the question.:(

---

### Post by Zack McCool on 2010-06-06
Any ideas?  Anyone?  ;)

Converting these manually, using avidemux, is a real pain.

I'd also be happy with configuration options for the mythbuntu box that would make the conversions unneccessary.

Basically, it is a System76 Meerkat Nettop Ion running mythbuntu 9.10.  The audio is connected to my stereo system using the coaxial digital output.  The stereo is 5.1, the videos not working right are AC3 6-channel.  I get music, and sounds, but no normal-conversation voices.  These are usually mapped to the center channel, so it makes sense that there would be a problem if the "center" isn't mapped right, for some reason.

So, ANY help would be great.  Either a simple cmd-line way to batch convert the audio in the Videos (generally Xvid AVI's) to MP3, or the right way to config the audio for the myth machine.

Thanks...
Joe

---

