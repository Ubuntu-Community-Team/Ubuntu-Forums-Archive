---
title: "How to CD-&gt;WAV(stereo)-&gt;MP3 in Linux?"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by registering on 2007-04-25
Hello. I'm running Edgy, and while Sound Juicer and Grip seem to almost get me what I need, I haven't found an app that can rip a CD to stereo WAV, and also convert from WAV to MP3. It would be great if the app also spoke to CDDB to get a CD's metadata so I don't have to type everything in. Am I missing codecs or a config somewhere? The best I found was ripping to mono WAV. :( Can I magically set channel=2 in some app to get stereo lossless (not OGG) working? Thanks for any suggestions!

---

### Post by renzokuken on 2007-04-25
why are you converting to WAV first then to MP3?

why not just go straight to mp3?

Sound Juicer is a good CD ripper

---

### Post by registering on 2007-04-25
I want a library of lossless formats (thus no MP3) recognized across many platforms (thus no OGG).

---

### Post by koshatnik on 2007-04-25
Audiograbber works well in wine - rips to WAV and then you can convert to mp3, or rip direct to mp3 and keep the intermediate WAV. looks like the best option for you.

you can download audiograbber from [here]("http://www.audiograbber.com-us.net/download.html")

Grab the lame codec as well, and extract and drop the lame.dll into the audiograbber directory in .wine

run winecfg in a terminal and make sure your cd rom drive is detected properly.

Et voila, you're ready to go.

---

### Post by registering on 2007-04-25
Thanks koshatnik. Are there any native Linux options? I'll gladly pay for a commercial app if one exists for Linux...

---

### Post by koshatnik on 2007-04-25
Grip is a decent linux ripper, but I only really use Audiograbber. Its fast, it does the job. Does it have to be linux native?

For me, audiograbber is yet to be beaten on any platform.

---

### Post by reclusivemonkey on 2007-04-25
> **registering said:**
> Hello. I'm running Edgy, and while Sound Juicer and Grip seem to almost get me what I need, I haven't found an app that can rip a CD to stereo WAV, and also convert from WAV to MP3. It would be great if the app also spoke to CDDB to get a CD's metadata so I don't have to type everything in. Am I missing codecs or a config somewhere? The best I found was ripping to mono WAV. :( Can I magically set channel=2 in some app to get stereo lossless (not OGG) working? Thanks for any suggestions!

You should be able to edit the GStreamer properties in any of the apps in Gnome which rip from CDs (Sound Juicer, which is the default, Rhythmbox, Banshee, etc.). Is there not a stereo wav option already included in there? I am at work right now so I can't check but all these programs should support stereo WAV and CDDB. Incidentally, do you have a CDDB server chosen? I think by default the menu option in preferences is disabled. You certainly don't need to use proprietary software.

---

### Post by registering on 2007-04-25
I could only find a mono WAV option, and I don't know how to set the channel to 2. I couldn't find how to do this in the user documentation, but I'm certainly hoping there's a way, as grip and sound juicer seem like really nice apps. I'm at work now also so I can't check, but I didn't see any options to alter/enter the CDDB server.

---

### Post by oleoleole on 2007-04-25
What about ripping to FLAC? :p Its lossless compression, and it holds ID-tags. Also its supported with Grip. You can also use an application called soundKonverter (KDE-app) to convert easily to most formats in different qualities. FLAC is supported by most plattforms, and a limit to handheld players. But else its easy to burn FLAC to ex. CDDA...

Wave is in most cases pretty useless...

---

### Post by registering on 2007-04-25
From what I remember of FLAC, it simply doesn't hold the amount of metadata as WAV (I know there's a long backstory as to why). Plus, it's simply not as portable as WAV. I don't agree that WAV is pretty useless. Thanks for telling me about soundkonverter though, I'll try that out.

---

### Post by koshatnik on 2007-04-25
TBH, if you really want WAV then audiograbber is the way to go in terms of ripping with ease.

---

### Post by registering on 2007-04-25
Just FYI, it looks like there's an option in Grip under Config->Encode->Options "Delete .wav after encoding". I will unselect this tonight and see if it leaves the .wav file around after encoding to mp3, which would give me both things at once (yay).

---

### Post by registering on 2007-04-25
Just FYI, deselecting it does exactly what it says, and I can even configure alternate CDDB servers, so grip does everything I'm looking for. Thanks to everyone for their help! :)

---

### Post by kweiner on 2007-04-28
This post shows how to create a lossless .wav profile in gstreamer:
[https://answers.launchpad.net/ubuntu/+source/sound-juicer/+question/2962](https://answers.launchpad.net/ubuntu/+source/sound-juicer/+question/2962)

I just tried it and it works great as far as I can tell.  I used Sound Juicer to rip some songs from a CD to WAV format.  Then I used Serpentine to burn the WAV files to a CD-R.

For some reason the songs play on computers and in my car CD player, but not on any of my older CD players at home.  I know very little about this stuff, so I have no idea what that is.

---

