---
title: "Missing Totem Sound for Real Media files"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by robulus on 2007-07-14
Hi folks,
When I setup Ubuntu a couple of days ago, one of the things I did was to try and play a Real Media file that I downloaded.  The Totem player opened up and suggested a couple of codec were needed to play it.  So I downloaded and installed them, but no joy - i was only getting audio, and no video.

So I left it for the time being, to do something more important, to setup totem to play encrypted DVDs, which now works just fine.(Huzzah!)

I came back, and ran totem on the same real media file, and now it's showing the real media video, but this time no audio.  Obviously the libraries I needed to get the DVD working must have included something to display the .rm files.

Anywho, any ideas where the audio went?  How to debug something like this?  Whether Totem needs some kind of extra configuration for .rm files?

Sound for everything else works - it's just missing from Totem for .rm files.

Totem's using the following codecs:
Audio :  RealAudio Cooker (ffmpeg) 
Video :  Real Video 4.0

Cheers!
Rob.

---

### Post by wolfen69 on 2007-07-14
try opening the file with VLC player. it works for me.

---

### Post by robulus on 2007-07-14
Hi there,
yeah I tried it on that player (VLC media player 0.8.6 (wxWidgets interface)) but the sound is all stuttering, and no video is displaying 8-/

Did you configure VLC in someway to get .rm files to work?
Thanks!
Rob.

---

### Post by wolfen69 on 2007-07-14
dont know if this will work, but
```
sudo apt-get install libxine-extracodecs
```

---

### Post by robulus on 2007-07-15
Hi again, and cheers for the reply.

I ran that command, downloaded and installed the package - my feisty installation was missing it.
However installing it didn't have any affect on either VLC or Totem (I'm using the xine backend for Totem).  The .rm files play as before, with video but no sound.

I don't suppose you could paste the codecs you use in VLC for real media files?

The .rm files I'm trying to view are here:
[http://www.lando.co.uk/](http://www.lando.co.uk/) in the sp section....

thanks!
Rob.

---

### Post by henryvann101 on 2007-07-15
SOLVED (for me at least) thanks to WOLFEN69.  Thanks Wolfen69!  My problem was that I couldn't get sound off the standard RealPlayer10 for Ubuntu Fiesty.  I just ran your command in Terminal and the sound was back!   (Only thing is I have to copy link location of said url location.)  But it works!  That's the main thing for me....

Hope this helps someone else...
Regards Ubuntu Bretheren/Sisteren

---

### Post by lemonedo on 2007-08-25
If you are using totem-xine, try this:
Open "~/.xine/catalog.cache" with any text editor you prefer and find "real_audio.so".
Then set its "decoder_priority" to "10", if it is not already 10.

---

### Post by balster neb on 2007-08-29
Thanks for the catalog.cache tip!

I too was unable to get sound on Feisty with totem-xine. It had worked fine with Edgy before this. I found this thread after Googling.

---

### Post by ernz on 2007-10-11
Thanks, this worked for me.

---

### Post by weigh2tall on 2007-10-21
> **lemonedo said:**
> If you are using totem-xine, try this:
Open "~/.xine/catalog.cache" with any text editor you prefer and find "real_audio.so".
Then set its "decoder_priority" to "10", if it is not already 10.

This worked for me too.  Thanks

---

