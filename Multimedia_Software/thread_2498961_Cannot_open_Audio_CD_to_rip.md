---
title: "Cannot open Audio CD to rip"
date: 2024-07-05
forum: Multimedia Software
---

### Post by starkiron on 2024-07-05
I try to open an audio CD so I can rip the tracks but I get this error:

0: No URI handler for the cdda protocol found

 
[LIST]
[*]Operating system: Ubuntu 24.04
[*]Strawberry Version: 1.0.23 installed through Ubuntu repositories
[/LIST]

Strawberry support said, "You are missing dependencies, most likely libgstcdio part of gst-plugins-ugly. You will be better off getting help through Ubuntu support."

---

### Post by Dennis N on 2024-07-05
Are you sure it is capable of ripping CDs? I don't see any mention of ripping tracks on their [list of features]("https://www.strawberrymusicplayer.org/#features").

Apps like **sound-juicer** are designed for ripping.

---

### Post by #&amp;thj^% on 2024-07-05
Along with what Dennis N has advised, here are a few more to read over: [https://www.slant.co/topics/2443/~best-cd-rippers-for-unix-like-systems](https://www.slant.co/topics/2443/~best-cd-rippers-for-unix-like-systems)

My choice is "ABCDE" I've just used it for many years now.

BTW I have never got Strawberry to rip CD's

EDIT: I forgot to mention if this not installed please do so:
```
 apt policy gstreamer1.0-plugins-ugly

```

---

### Post by starkiron on 2024-07-05
> **Dennis N said:**
> Are you sure it is capable of ripping CDs? I don't see any mention of ripping tracks on their [list of features]("https://www.strawberrymusicplayer.org/#features").

Apps like **sound-juicer** are designed for ripping.

Ah, you are right. I was confused because they have a "Transcoding" feature which I thought was for ripping.

Sound Juicer will not rip to 320 kbps mp3 which is what I want to do.

---

### Post by starkiron on 2024-07-05
Will ABCDE rip mp3 to 320 kbps and also find and label the track names?

Asunder and sound juicer will not rip to 320 kbps mp3.

---

### Post by #&amp;thj^% on 2024-07-05
> **starkiron said:**
> Will ABCDE rip mp3 to 320 kbps and also find and label the track names?

.
For that I use:
```
abcde -o 'flac:-8,mp3:-b 320' -G
```
My complete install is this:
```
 sudo apt-get install abcde cd-discid lame cdparanoia id3 id3v2

```

What this means is that you can run abcde from the command line, without any options, and expect it to rip and encode all the tracks on a CD. By default, Abcde will complete the following tasks: cddb, read, encode, tag, move, and clean.

---

### Post by #&amp;thj^% on 2024-07-05
To be fair "ripperx will do it all"

---

### Post by TheFu on 2024-07-05
+1 for abcde. I used it to re-rip my multi-thousand disc collection. 

This time, I kept FLAC and Vorbis 192 kbps.  MP3 is so 1990s.  With my best Shure cans, I cannot hear the difference between FLAC (compressed+lossless) and Vorbis-192.  

If you are an Apple house, AAC-192 is probably equivalent, but not F/LOSS.  Pretty much any player supports Vorbis audio these days ... Google and Spotify both use it for their video and audio streams.

---

### Post by starkiron on 2024-07-05
I would like a variable bitrate. Is that command a constant or variable bitrate?

---

### Post by starkiron on 2024-07-05
What provides the best quality audio?

1. Rip audio CD to FLAC and then transcode to 320 kbps variable bitrate mp3?
or
2. Rip audio CD directly to 320 kbps variable bitrate mp3?

Thank you for the Vorbis tip. I will look into that. I would need to know if my Volkswagen will play Vorbis files from USB drives and SD cards. MP3 is most universally accepted.

---

### Post by #&amp;thj^% on 2024-07-05
I find flac to be one of the best possible play back quality option.

FLAC stands for Free Lossless Audio Codec, and it&#8217;s a digital audio file format like MP3, but with a significant, important difference: it is a lossless file type &#8212; meaning that no audio data is discarded during the encoding process. This results in significantly larger files than MP3, but you can rest assured that there&#8217;s no detail missing from the files you&#8217;re hearing. Audio purists are drawn to FLAC because it leaves the recording untouched. Additionally, FLAC supports a range of bit depths and sampling rates that go high enough to satisfy all your hi-res desires.

---

### Post by starkiron on 2024-07-05
I have already ripped all my cd's to FLAC but they won't play in my Volkswagen and I also want a separate audio library that has a smaller size. I definitely agree that FLAC is best but it doesn't always play with some tech.

---

### Post by TheFu on 2024-07-05
Audio CDs store everything as WAV files.  Going from WAV--> FLAC --> whatever only makes sense if you actually keep the FLAC files.  We all love re-ripping audio CDs, but if you don't, then having a lossless, compressed, F/LOSS version of everything is handy.

Going from FLAC or WAV to mp3 doesn't matter.  If you only want MP3 and no other output, then I wouldn't bother with FLAC.  I was young once and regret NOT having a lossless format for my music collection.  20+ yrs later, I corrected that.  Only you can decide if it is worth it now or not.  OTOH, having the lossless format on disk let's you convert to other formats as you decide whether mp3 is worth it to you or not.  In a car, does it really matter to have 320 kbps MP3 files?  Road noise will hide all of that.  I'd say that even 160 Kbps mp3 in a moving vehicle is overkill.

Before you decide which container and encoding to use, you'll definitely need to test it.  In my 20+ yr old car, I have a CD player that does mp3 and wma files off data CDs.  Of course, it will play normal music CDs too, but I wouldn't want to risk those in a hot car all summer. ** For the last 20 yrs, I've used an AUX input from either a music player device or a phone/tablet to playback stuff in the car.**  I don't do bluetooth (poor security), so the 2.5mm input jack is used. Works perfect and anything my phone can play, I can listen to in the car.  I do have about 20 data CDs from 20+ yrs ago in the vehicle for times when I just want something and nothing specific.  About once a year, I'll swap in a different CD.

If you have a media server at home, you might want to verify that the formats work with it.  For example, Plex has a very narrow list of supported audio files. There are better media servers that seem to support every possible type, so not using Plex really isn't a hardship. Plus the F/LOSS media servers don't sell us out like Plex does.  What we listen to and what we watch isn't the business of anyone, right?

---

### Post by #&amp;thj^% on 2024-07-05
I run my collection thru my phone to the player/tuner in my Subaru. I got tired of what your now facing.
Particularly when traveling.

---

### Post by starkiron on 2024-07-05
Thank you for the detailed reply. I have a FLAC library of all my CDs's, so I'm good with that.

Now my issue is compatibility and file size but optimizing quality.

Is it better to rip an audio cd to FLAC and then transcode to mp3 or rip the audio CD directly to mp3 for the best audio quality?

---

### Post by starkiron on 2024-07-05
> **1fallen said:**
> I run my collection thru my phone to the player/tuner in my Subaru. I got tired of what your now facing.
Particularly when traveling.

I'm currently having issues connecting my Android phone directly to my VW which only has USB-C ports and an SD slot. I no longer want to use bluetooth. Nothing will play through my phone but that's an issue for another tech support forum.

So for now, I just want to copy and paste my library of mp3 to an SD card or USB drive to play in my car.

---

### Post by TheFu on 2024-07-05
If you already have FLAC, why are you ripping anything again?  Completely unnecessary.

---

### Post by starkiron on 2024-07-05
I have asked the same question twice but haven't gotten an answer yet. My questions should answer your question as to why I'm considering ripping.

---

### Post by TheFu on 2024-07-05
> **starkiron said:**
>  Is it better to rip an audio cd to FLAC and then transcode to mp3 or rip the audio CD directly to mp3 for the best audio quality?

Perhaps this isn't clear.  Since you've already ripped everything to FLAC, it would be best to just use the FLAC files to create whatever lossy format you decide and avoid the re-ripping completely.  FLAC quality and CD-source quality are identical.  That's the point of FLAC.  Also, by avoiding reading from optical media the transcoding will be much faster. Reading optical media is slow. Very slow by standards today.  

There are lots of ways to transcode from FLAC to MP3 or AAC or Vorbis or ... whatever.  Pick your tool of choice.

Quality isn't any different between using FLAC or re-reading from the optical CD, so that doesn't matter. It is just about convenience. Does that more clearly answer the question?

Here's an easy way to feed a list of filenames (no spaces allowed!), into a script that will convert from any 3 character extension to a vorbis encoding inside an ogg container: 
```
$ more ~/bin/toOgg
#!/bin/bash

for filename in "$@"; do
   ROOT="${filename/%.???/}"
#   oggenc -b 192 -o "$ROOT.ogg" "${filename}"
    ffmpeg -i "${filename}"  -vn -codec:a libvorbis -qscale:a 6 -vn "${ROOT}.ogg"
done

```

To do an entire directory, I'd use 
```
$ toOgg *aac
```

It wouldn't take much to do it for FLAC. Actually, flac files will work too, but you'll probably want to remove the flac that would be left inside the file name.   Originally, I used oggenc, but it supports limited input file types, so the switch to ffmpeg was made to support any audio/video file type that ffmpeg supports ... which is basically all of them.

The quality of '6' turns into a Vorbis encoding at 192kbps.

I'll leave the ffmpeg command for mp3 output for you to figure out. ffmpeg has lots of documentation, so pretty much anything is possible.

BTW, at very low bitrates, opus is supposed to be better than Vorbis.  I'm unsure where the cross-over for "better" is between opus and vorbis .... or if any actually exists anymore.  Opus has been the newer audio codec for some time.  I've seen it for voice - telecom and audiobooks mostly.  If Opus is "better quality" than Vorbis at the same bitrate, I'd transcode everything I have a flac today to opus.  Since all my players are either Linux or Android, I don't have to worry about compatibility.  Of course, YMMV.

---

### Post by Dennis N on 2024-07-05
> **starkiron said:**
> What provides the best quality audio?
1. Rip audio CD to FLAC and then transcode to 320 kbps variable bitrate mp3?
or
2. Rip audio CD directly to 320 kbps variable bitrate mp3?


As a rule, I've read that each conversion step to another format can degrade the quality slightly. Theoretically, #2 should be better, but you may not notice any difference. Only you can decide.

One thing about VBR mp3. The track duration displayed by the player may be incorrect when it has to be calculated by the player.

---

### Post by ajgreeny on 2024-07-06
And another vote here for **abcde** which I have used for many years, though no longer as I have no working CD drive now on any machine.

I used to rip to mp3 as that was the only audio format playable on my very simple, cheap audio player but stopped using mp3s when my mobile phone became my mobile audio device and moved to flac.

With the appropriate abcde.conf file the command **abcde** did all that was needed to rip to flac. Quick and simple with no unnecessary GUI.

---

### Post by starkiron on 2024-07-06
> **TheFu said:**
> The quality of '6' turns into a Vorbis encoding at 192kbps.

Thank you for so much detail in your response. It sounds like Ogg Vorbis 192kbps is better than 320kbps mp3 so I will experiment with that to see if my VW will play that file type from SD cards and USB drives.

I see soundconverter will transcode to 256kbps Ogg Vorbis. Is there any advantage to going a bit higher in quality or won't my ears notice a difference?

---

### Post by starkiron on 2024-07-06
> **ajgreeny said:**
> but stopped using mp3s when my mobile phone became my mobile audio device and moved to flac.

How do you manage to store all your FLAC audio on a mobile device? Just one FLAC album of mine averages around 1GB of data so that doesn't leave much room for many albums on a phone these days. Unless you are using a phone that can add large amounts of storage?

---

### Post by ajgreeny on 2024-07-06
> **starkiron said:**
> How do you manage to store all your FLAC audio on a mobile device? Just one FLAC album of mine averages around 1GB of data so that doesn't leave much room for many albums on a phone these days. Unless you are using a phone that can add large amounts of storage?
I have a phone with 128G memory and could add a micro-SD card if necessary (not required yet). When driving in the motor I listen mainly using Android-Auto on the car stereo system or  when not driving using bluetooth ear-pods.

Perfect for my needs.

---

### Post by TheFu on 2024-07-06
> **starkiron said:**
> Thank you for so much detail in your response. It sounds like Ogg Vorbis 192kbps is better than 320kbps mp3 so I will experiment with that to see if my VW will play that file type from SD cards and USB drives.

I see soundconverter will transcode to 256kbps Ogg Vorbis. Is there any advantage to going a bit higher in quality or won't my ears notice a difference?

We all have different ears.  As you get older, more and more cumulative damage, specific to what you've done or been exposed to will change what you can hear.  Your ears will never be as good as they were around age 13. It's all downhill from there.  My point is that "hearing" is subjective, so only you can decide which audio-codec and bit rates sound good to you.  The question of "good enough" or "better" is also subjective.  

Nobody else can say what your ears hear or what you like.

So, lacking that, if you don't want to do the listening work for yourself, I can only suggest picking 10-20 sample tracks (different types of music!) and transcoding those into the possible options of audio encoding and bitrates you would consider.  If it were me, thinking as you, I'd start with FLAC, create 320, 256, 192, 160 Kbps MP3.  You seem to be interested in Vorbis.  I'd start at 256, 192, 160 Kbps vorbis.  Create all the tracks with all those possible encodings and listen to 1 track starting with the FLAC going down in quality, until you hear something that doesn't match in each encoding (mp3/vorbis/other).  If you can tell the difference between 256 and 320 Kbps MP3, then 320Kbps is your minimal MP3 bitrate. I seriously doubt you will hear any different. Almost nobody can tell the difference between 256 and 320 mp3 files.  

For vorbis, I suspect you cannot hear the difference between 160Kbps and anything higher, but only your ears and listening can answer that question.

The more sample tracks you try, the more likely you are to find different answers for the bitrates of each.  The goal is to find the lowest bitrate that matches the FLAC source file for each sample and encoding.  Make a spreadsheet to keep track.  Listen with your best headphones through your best audio equipment, in a quiet environment at a reasonable volume for enjoyment.  For example, I like to listen to either acoustic guitar or classical music on Sunday mornings while reading the newspaper.  Most days, I'll listen to rock or pop or country all day long at low volumes while I work.  It is mostly background noise, with a few breaks to really appreciate specific songs.

Anyway, for me, I couldn't tell the difference between FLAC and 192 Kbps Vorbis.  These files are smaller than mp3 by 10-30% and I think 256 kbps mp3 would be just as good for my ears, but the mp3 files would be 2x the size.  YMMV.

It should go without saying, but transcoding from a lower quality to a higher quality doesn't work. It makes the flaws more pronounced.

Hope that helps with your decision process. Only you can decide.

---

### Post by starkiron on 2024-07-06
Ok, so my VW will not play Ogg Vorbis or FLAC so I'm stuck transcoding to mp3. I'm just going to stick with FLAC for all my audio at home and mp3 320kbps for my car. Thanks for all your help and suggestions.

---

### Post by qyot27 on 2024-07-06
> **TheFu said:**
> BTW, at very low bitrates, opus is supposed to be better than Vorbis.  I'm unsure where the cross-over for "better" is between opus and vorbis .... or if any actually exists anymore.  Opus has been the newer audio codec for some time.  I've seen it for voice - telecom and audiobooks mostly.  If Opus is "better quality" than Vorbis at the same bitrate, I'd transcode everything I have a flac today to opus.  Since all my players are either Linux or Android, I don't have to worry about compatibility.  Of course, YMMV.
It's 10 years old, but there is this (back when HydrogenAudio and Doom9 regularly had multiformat audio listening tests, which I've not seen in a long time when I started thinking about it):
[http://listening-test.coresv.net/results.htm](http://listening-test.coresv.net/results.htm)

The test was at 96kbps, and Opus was almost always in the #1 spot, followed by Apple's AAC encoder in #2, and aoTuV-patched Vorbis at #3, with only a few times where the order of the top three differed.  I'd be surprised if there has been any change in position since then, except for there being further refinements made to Opus, as 2014 was fairly early in its lifecycle, and Xiph.Org already considered Vorbis deprecated.  You only need to go back three or four pages on the libvorbis git repo to get to where deeper-ish parts of the code were getting changes in ca. 2013-2015, but nearly everything in the time after that has been refinements to the build system/CI-related stuff that has nothing to do with the actual coding tools.

Technically-speaking, Opus is a hybrid of two different coders - SILK, a low-latency speech codec, and CELT, which was being developed as the successor to Vorbis.  I can't remember how low the exact point is where Opus switches from CELT-derived tools to the SILK-derived ones, but 96kbps is comfortably within CELT territory.

And obviously, 96kbps isn't where most people making CD backups are encoding their files.  It's well above that, even greatly exceeding the point where most of these formats hit perceptual transparency for most types of audio content.  MP3 generally is transparent around 192kbps, but how often do people crank it up to 256-320kbps or simply CQ0 for variable rate encodes?  Same deal with AAC, Vorbis, and Opus, with the difference that those formats can support higher channel counts; not that that matters for CD rips, though.  Trying to optimize transparency down to lower and lower bitrates has become less and less important as storage costs have gotten stupidly cheap (or mobile Internet allowing greater bandwidth/speed for at least **better** cost than 10 years ago).  The differences generally start to be seen in how the formats handle their failure states and how annoying their particular artifacting is on the off times that it actually appears.

Personally, I make all my CD backups in single-track FLAC+CUE, and split-track AAC and Opus @~192kbps (the 'greatly exceeding' transparency bit I just mentioned...).  To be completely honest, the AAC copies are simply for historical precedent and at this point I could just omit that one entirely.  I added Opus copies to the process back in 2013.

> **Dennis N said:**
> As a rule, I've read that each conversion step to another format can degrade the quality slightly. Theoretically, #2 should be better, but you may not notice any difference. Only you can decide.
Generational decay only happens for conversions from lossy formats to lossy formats.  FLAC is lossless.

> **starkiron said:**
> Just one FLAC album of mine averages around 1GB of data
The PCM stream from a CD cannot exceed ~800MB (~74 mins.) in size as a limitation of the CD format itself, and FLAC will always be smaller than that given the same attributes.  Especially so if you use the highest compression level.

44.1 kHz x 2 channels x 16-bit depth = 1411.2kbps raw throughput x 4440secs (74 mins.) = 6,265,728 kbits / 8 = 783,216 kilobytes (764,859 kibibytes)

If sourced from a DVD-Audio disc, it could be higher, due to higher frequency, channels, and bit depth, but not from a CD.

---

### Post by qyot27 on 2024-07-06
> **starkiron said:**
> Ok, so my VW will not play Ogg Vorbis or FLAC so I'm stuck transcoding to mp3. I'm just going to stick with FLAC for all my audio at home and mp3 320kbps for my car. Thanks for all your help and suggestions.
I just use an FM Bluetooth adapter to hijack the radio in my 93 Celica.  It plugs into the cigarette lighter.

---

### Post by TheFu on 2024-07-06
> **starkiron said:**
> Ok, so my VW will not play Ogg Vorbis or FLAC so I'm stuck transcoding to mp3. I'm just going to stick with FLAC for all my audio at home and mp3 320kbps for my car. Thanks for all your help and suggestions.

Yep, hardware support breaks the greatest ideas! 

Hopefully, you will be happy with your choice for a long time.

---

### Post by starkiron on 2024-07-06
> **qyot27 said:**
> I just use an FM Bluetooth adapter to hijack the radio in my 93 Celica.  It plugs into the cigarette lighter.

I am currently working to eliminate Bluetooth from all my tech, so I want everything wired or played from hard disk media.

I appreciate the long response with all the details about sound quality and codecs. Based on what you and others have said, If one is going to use a codec other than FLAC, Opus is the way to go, but compatibility may be the sticking point.

This whole conversation has me missing the days of cd's and my old iPod. Just run an AUX cable from the iPod into the car and I was up and running. No Bluetooth instability and loss of quality, Android Auto, compatible apps with "permissions" to harvest everything I do, and my new VW can't even play any codecs other than mp3.

Right now, I can't even just run a USB-C cable from my Android phone into my VW and just play music. That doesn't even work! I have to use Android Auto and Bluetooth, neither of which I want to use.

---

### Post by 909mjolnir on 2024-07-08
in some linuxes, the CD tracks just show up in file manager as WAV files, and then you can copy them.  
that's what I have in one of the Arch Linuxes.  Also, somebody invented an FFMPEG file system, yeah really. 

ffmpegfs

---

