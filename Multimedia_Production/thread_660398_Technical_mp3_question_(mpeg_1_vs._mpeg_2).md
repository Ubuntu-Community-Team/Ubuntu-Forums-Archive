---
title: "Technical mp3 question (mpeg 1 vs. mpeg 2)"
date: 2008-01-06
forum: Multimedia Production
---

### Post by mjpatey on 2008-01-06
Hi, all-

I convert my church's sermon recordings from CD to mp3 for upload to our website.  Back when I was using Windows, I'd open the CD in Adobe Audition, and save it as an mp3 at 44.1KHz, 64Kbps, mono.  It would play back just fine everywhere, and people could burn them to CD with no problems.

Well, since switching to Ubuntu, I've been using ffmpeg to do the conversion, with the SoundKonverter front end.  It lets me specify a custom ffmpeg pipeline, which allows me to get the weird attributes mentioned earlier (44.1KHz, 64Kbps mono).

Unfortunately, since switching to this method, people can indeed play back the mp3 files, but nobody is able to burn them to CD!

So in Nautilus, I right-clicked on one of my files and found that they're all MPEG-1, Layer 3.  I always thought mp3s were MPEG-2, Layer 3.  Upon researching, I found the chart on the following page:

[http://www.humanvalues.net/podcasting/]("http://www.humanvalues.net/podcasting/")

Which seems to show that an MPEG encoder, when asked to create a file with my specs, will make an MPEG-1 file, rather than MPEG-2.

If that's the case across the board, then Adobe Audition would create the same kind of file, and that couldn't be the problem.  I wish I were at my Ubuntu computer so I could test some of the files I made in Windows to see if it, too, is an MPEG-1, but I can't right now.

Can the fact that an mp3 is encoded as MPEG-1 rather than MPEG-2 cause it to not be recognizable by CD burning software?  Or is there some other aspect of my mp3s that is causing them not to be able to be burned?

Three different Windows programs were used to try to burn the ffmpeg-created files to CD, and none worked... they were Nero, Windows Media Player, and something I've never heard of.

So the overall question is... how do I create a 44.1KHz 64Kbps Mono mp3 in Ubuntu that can be burned to CD in Windows?

Thanks for any insight you may have!

-Mark

---

### Post by mcduck on 2008-01-06
MP3 file _is_ MPEG-1 layer 3 by standard, and that _should_ work on every machine.

MPEG-2 format added support for more than 2 audio channels but otherwise MPEG-2 layer 3 is just the same thing, and should be fully backwards compatible with MP3.

Perhaps you should try some different encoder than ffmpeg. Lame, for one, is very good and might work better.

I've never used SoundKonverter, but if it doesn't allow you to use lame then I recommend using Grip as the ripper.

---

### Post by mjpatey on 2008-01-06
Thanks for the suggestion!  I'll give that a shot tonight.

If I'm not mistaken, I think SoundKonverter allows gstreamer or ffmpeg, but I'm not sure about LAME.  I will check, and give that a try before trying out Grip.

Thanks again!

-Mark

---

### Post by disturbed1 on 2008-01-07
Just use SoundJuicer the default audio CD ripper in Ubuntu. It uses GStreamer (which has a lame plugin) you can edit the profiles, and/or create new ones.

---

### Post by mjpatey on 2008-01-07
disturbed1... thanks for the recommendation.  But this is where it all falls apart for me.  I can find no documentation or tutorials that will show me how to create the "Gstreamer pipeline" to take audio from, say, CDDA to a 44.1KHz mono mp3 at 64Kbps.

Does anyone have enough expertise to be able to just tell me what to type into that field?

I also need to be able to do the same with a WAV file... take a WAV as input and convert it to a 44.1KHz mono mp3 at 64Kbps.

So far, everything I've tried barfs on me in one way or another.  I'd be fine if my needs were simple (i.e., ripping a music CD to "CD Quality mp3"), but my strange parameters seem to require manual tweaking, and I just don't know how to do it.

Any experts on gstreamer or ffmpeg pipeline switches?  Or can you point me to a resource that lists these?

Thanks, all!

-Mark

---

### Post by disturbed1 on 2008-01-07
It's easier than you tink ;)

For the whole meat -
 gst-inspect-0.10 lame

So, if you take the default profile -
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

We need to edit inbetween **enc** and **!** so change this _mode=0 vbr-quality=6_ to what you need.

vbr=0 bitrate=64 quality=0 mode=3 
That's it.

Your complete pipeline would then read

audio/x-raw-int,rate=44100,channels=1 ! lame name=enc vbr=0 bitrate=64 quality=0 mode=3 ! id3v2mux

This will cause SoundJuicer to rip your CD to 44100hz mono mp3 using lame to encode a mono mp3 at 64kb/s.

---

### Post by mjpatey on 2008-01-07
That's the kind of info I was looking for!  Thank you!

Is there somewhere online that lists all this for shlubs like me who haven't a clue?  All I can find are reference manuals for programmers... and I think we've established that I'm not one of those.  :-)

-Mark

---

### Post by disturbed1 on 2008-01-07
Google knows everything :D

All I did was a google search for "create custom gstreamer pipeline"

---

### Post by mjpatey on 2008-01-07
disturbed1,

It made a 64Kbps mono mp3, woohoo!  Now to see if my Windows people can burn it to a CD... Hey, do you know of a way to do the same thing with a WAV file as the source rather than CD?

Thanks again!

-Mark

---

### Post by mjpatey on 2008-01-07
I googled "gstreamer pipeline" and "...tutorial" etc.  I'll keep looking.

---

### Post by disturbed1 on 2008-01-07
only in command line :(

lame -a -m m -q 0 -b 64 --cbr input.wav output.mp3

-a downmixes stereo to mono
-m m sets the mode to mono
-q 0 sets the quality to 0 (highest/slowest)
-b 64 sets bitrate to 64
--cbr enforces constant bitrate.

Got a folder full of wavs?

for i in *.wav; do lame -a -m m -q 0 -b 64 --cbr "$i" "$i.mp3"; done

---

### Post by disturbed1 on 2008-01-07
> **mjpatey said:**
> I googled "gstreamer pipeline" and "...tutorial" etc.  I'll keep looking.

[http://www.google.com/search?q=gstreamer+lame+pipeline&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=gstreamer+lame+pipeline&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

4th link

[http://bluwiki.com/go/GStreamer](http://bluwiki.com/go/GStreamer)

---

### Post by disturbed1 on 2008-01-07
> **mjpatey said:**
>   Now to see if my Windows people can burn it to a CD... 

-Mark

I was thinking (:lolflag: )



The problem may just not be with your mp3/mp2 files in the first place, but whatever program the users are using to burn the CD. ***Perhaps*** the problem is that they are mono files, and CD-AUDIO is stereo, and the programmer just never thought of including a way to convert the mono file into a stereo one?

Nero for Windows and NeroLinux both had this problem at some point in time. Just a thought.

---

### Post by mjpatey on 2008-01-08
That's probably not the case, because the programs are able to burn earlier mp3s of the same spec that I created in Windows.  The burning apps that all show this same behavior in Win XP are Windows Media Player (not sure which version/s), Nero, and a third that I can't remember.

I really appreciate your help with this.  I'm very happy to do it via command line if that's what works, so I will give it a shot.  Thanks again!

-Mark

---

### Post by mjpatey on 2008-01-08
I just noticed the new "Thanked x Times in x Posts" feature... do you know how I'd go about "officially" thanking you, or does the forum software pull it automatically from the text of our posts?  I can't seem to find it anywhere.

---

### Post by disturbed1 on 2008-01-08
Right next to the quote button ;)

---

### Post by mjpatey on 2008-01-08
...and you have been thanked!

I'm playing around with the parameters given in the output of "gst-inspect-0.10 lame".  And I'm about to try that mini-script to convert a gaggle of WAVs to my little mono format.

-Mark

---

### Post by mjpatey on 2008-01-08
disturbed1, I just ran the mini-script from post #11 in a folder full of short WAVs, and it seemed to be running (quite impressively).  But when I try to access that folder in Nautilus, for some reason, it now says its contents can't be displayed.

I also can't test the files in the command line because the source WAVs (and now their mp3 counterparts) contained spaces, and I can't type, for example, "mplayer hello this is my space-containing filename.mp3".

Any idea what might have gone wrong?  Do you think the spaces in the filenames made the source WAVs unappetizing to lame?

Thanks for all your help... I'd be nowhere on this without it!

-Mark

---

### Post by mjpatey on 2008-01-08
OK, I just did a ctrl-alt-backspace, because suddenly every directory on my machine was giving me the same message!  I don't know what happened, but it seems not to have been related to the mp3 operation.

After the restart, all's well!  I can play the WAVs and the brand-new mono mp3s with no trouble at all!  And a right-click on the mp3s in Nautilus shows the properties as being MPEG-1 Layer III 44.1KHz Mono, 64Kbps.  :)

Thanks again!!!   :guitar:

-Mark

---

### Post by disturbed1 on 2008-01-08
The spaces are the reason for the **"** around $i.

Not sure why mplayer won't play the files?

For nautilus, kill it one of 2 ways
system monitor, right click on nautilus kill process
in the term - killall nautilus

Either way nautilus will close and relaunch. Nautilus seems to have issues with file monitoring in *active* directories.

---

### Post by mjpatey on 2008-01-08
For anyone else who is looking for this info, I found the complete list of "lame" mp3 encoding command line switches here:

[http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/switchs.html]("http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/switchs.html")

In Ubuntu you'd install lame with:

```
sudo apt-get install lame
```

...and that would allow you to run either of the conversion scripts given by disturbed1 in post #11, and you can tweak it to your particular options using the command line switches in the link above.

-Mark

---

### Post by disturbed1 on 2008-01-08
lame --longhelp ;)

It should be noted that the gstreamer pipeline differs from using straight lame in the command line. To get those commands it's (again)
gst-inspect-0.10 lame

You can use gst-inspect-0.10 codecname to get the options to any gstreamer codec.

---

### Post by mjpatey on 2008-01-08
Ah, I see!  That's a strange problem.

I think our posts crossed in the mail... you can see how my weird Nautilus issue resolved in the post above yours (#19).  My fix was probably overkill, but it worked.  :-)

All that's left now is for someone to test whether they can burn these mp3s to an audio CD in Windows... I think it's time to call my wife at work.  :-)

-M.

---

