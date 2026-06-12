---
title: "Rhythmbox/gstreamer: FLAC option not appearing in &quot;Preferred Formats&quot;, can't add"
date: 2009-12-15
forum: Multimedia Software
---

### Post by Jayferd on 2009-12-15
Hey all,

So I was re-ripping my cd library yesterday in Rhythmbox (I accidentally wiped my external drive a few weeks ago), and it worked fine for about 15 cd's, but then I ran an update and it seems it forgot how to encode flac.  The option was completely missing from the "Preferred Formats" menu under Preferences -> Music.

The weird part was that neither rhythmbox nor any gstreamer packages were updated:

```

The following packages will be upgraded:
  app-install-data-partner apport apport-gtk chromium-browser 
  chromium-browser-inspector chromium-codecs-ffmpeg libpython2.6 
  python-apport python-problem-report python2.6 python2.6-minimal 

```

I looked around and ended up reinstalling gstreamer0.10-plugins-good, but that didn't change anything either.

Lastly, I tried adding the "flac" profile manually, copying over from another ubuntu machine; but it still didn't appear in the menu, so I couldn't test it.

Is there a package I need to downgrade?  A new package I need to install?  How can I get rhythmbox to rip my cds in flac again?

---

### Post by howefield on 2009-12-15
Check you have flac installed. Fire up synaptic and search for it.

---

### Post by Jayferd on 2009-12-15
Ah, yes, I forgot to mention.  I did install flac after this happened (sudo aptitude install flac), and it didn't change anything.

Thanks for the reply, though!

---

### Post by Jayferd on 2009-12-16
...I also tried opening Sound Juicer, and it says "The current audio profile is not available on your installation", with no hints as to how to make it so!  erg!

---

### Post by Yellow Pasque on 2009-12-16
Hmm, maybe try this command and see if it lists flac:
```
$ gst-inspect-0.10 | grep flac
```
Output on my box looks like:
```
ffmpeg:  ffdec_flac: FFmpeg FLAC (Free Lossless Audio Codec) decoder
ffmpeg:  ffmux_flac: FFmpeg raw FLAC muxer
typefindfunctions: application/x-id3v2: mp3, mp2, mp1, mpga, ogg, flac, tta
typefindfunctions: application/x-id3v1: mp3, mp2, mp1, mpga, ogg, flac, tta
typefindfunctions: audio/x-flac: flac
flac:  flacenc: FLAC audio encoder
flac:  flacdec: FLAC audio decoder
flac:  flactag: FLAC tagger
```

---

### Post by Jayferd on 2009-12-16
Looks pretty normal: 

```

typefindfunctions: audio/x-flac: flac
typefindfunctions: application/x-id3v1: tta, flac, ogg, mpga, mp1, mp2, mp3
typefindfunctions: application/x-id3v2: tta, flac, ogg, mpga, mp1, mp2, mp3
ffmpeg:  ffmux_flac: FFmpeg raw FLAC muxer
ffmpeg:  ffdec_flac: FFmpeg FLAC (Free Lossless Audio Codec) decoder
flac:  flactag: FLAC tagger
flac:  flacdec: FLAC audio decoder
flac:  flacenc: FLAC audio encoder

```

Peace,
--Jay

---

### Post by mc4man on 2009-12-16
Take a look here and see if it's active and if the pipeline command is correct
```
gconf-editor
```

---

### Post by Guitar John on 2009-12-16
If all else fails, create a new profile:
Edit > Preferemces > Music (tab)

Click on the "Edit" button.

When the menu opens, click on the "New" button.

Name the new profile "CD Quality, Lossless"

Highlight the new profile and click on the "Edit" button.

In the box that says GStreamer pipeline:
```
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc

```

In the box that says File extension:
```
flac
```

Tick the button that says "Active?"

Click on the "Close" button.

You should now have an option in the menu for CD Quality Lossless.  Choose it.  Close Rhythmbox, and re-open.  

You're done.

---

### Post by Jayferd on 2009-12-16
Ah, maybe I didn't make it clear.  What I meant by "can't add" is that if I add a profile and click the "Active" checkbox, it still doesn't appear in the dropdown list of available formats in Rhythmbox.  I would take a screenshot, but whatever screenshot thing I have doesn't work when a menu is open.

...so yes, I have a flac profile, and it looks just like that, and I have flac installed, but Rhythmbox seems not to know it.  ...?

Thanks for all your helpful responses so far though, I really appreciate you guys taking the time to help me.

---

### Post by Jayferd on 2009-12-17
Here's my gconf-editor, too.

---

### Post by Jayferd on 2009-12-17
okay, now it's not playing anything.  I'm thinking of doing a hard reinstall, see if that fixes it.  But I want to make sure this is weird enough for that first.

--Jay

EDIT: D'oh.  The speakers were uplugged.  Posted too soon.  But I'm still considering a fresh install because I can't rip to flac.  I'm on 64-bit, if that makes any difference.

---

### Post by Yellow Pasque on 2009-12-17
What is that custom key in the screenshot? Try removing that.

Also, can you play a flac file using gst-launch0.10?
```
gst-launch-0.10 filesrc location=<filename> ! flacdec ! audioconvert ! audioresample ! pulsesink
```

Oh, sorry, it's an encoding issue, not a decoding issue. :\

---

### Post by Jayferd on 2009-12-17
That last one is a profile I created after the other one stopped working.  I'm not sure how to delete the thing, but I deleted all its keys.

Also, I can play flac files in Rhythmbox, but when I tried that command it gave me an error; maybe I typed it in wrong?

```

self@samadhi:~/Music/Sonny Rollins/Without a Song - The 9-11 Concert$ gst-launch-0.10 filesrc location=<01\ -\ Without\ A\ Song.flac> ! flacdec ! audioconvert ! audioresample ! pulsesink
ERROR: Pipeline doesn't want to pause.

```

---

### Post by carlotheman on 2010-07-25
I just had this problem on Lucid Lynx, so I'll add my solution in case any one Googles this.

Apparently Rhythmbox checks the following gconf setting to populate the list:

system -> gstreamer -> 0.10 -> audio -> global -> profile_list

In this list, cdlossless was missing. I have no idea how that happened (something about ejecting the CD while rhythmbox is ripping), but entering it back in there solved the problem.

---

### Post by AbdRahim on 2012-02-24
cdlossless is present on oneiric.  How ever still no flac listed in rhythmbox.

---

