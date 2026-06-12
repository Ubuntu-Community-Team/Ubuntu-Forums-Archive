---
title: "Ubuntu 9.10 not playing mp3, not sending sound through audio jack"
date: 2010-01-03
forum: Multimedia Software
---

### Post by Aldentron on 2010-01-03
I upgraded to Ubuntu 9.10 recently to find that my computer will not play mp3 files in Rythmbox, Amarok, or Kaffeine media players.  All of the FLAC files I have ripped from CDs work, but no mp3 files work.  I have downloaded and installed the ubuntu restricted codecs from Synaptic as well as the codecs prompted by Rythmbox, rebooted, and still no result.

Like I said, the .FLACs play fine.

On another note, no sound is being transmitted to my earbuds.  The only sound will come from the laptop speakers.  I went into ALSAmixer and turned everything except microphone up and made sure nothing was muted, and still nothing will play out of the earbuds.

---

### Post by Yellow Pasque on 2010-01-03
Try to play an mp3 from the command line. Replace 'test.mp3' with the path to your mp3. If you're not running Pulseaudio, try 'alsasink' or 'osssink' instead of 'pulsesink'
```
sudo apt-get install gstreamer0.10-tools libxine1-plugins
cd <your music directoy>
gst-launch-0.10 filesrc location=test.mp3 ! decodebin ! audioconvert ! audioresample ! pulsesink
```

---

### Post by Aldentron on 2010-01-03
After submitting the first command in Terminal, I get this message
```
gstreamer0.10-tools is already the newest version.
E: Couldn't find package libxinel-plugins

```

When I enter the second command:
```
alden@alden-laptop:~$ cd <Music>
bash: syntax error near unexpected token `newline'

```

And the third command:

```
alden@alden-laptop:~$ gst-launch-0.10 filesrc location=BoardsofCanada>BocMaxima>02chinook.mp3 ! decodebin ! audioconvert ! audioresample ! alsasink

(gst-launch-0.10:2406): GLib-WARNING **: g_set_prgname() called multiple times
ERROR: Pipeline doesn't want to pause.
```

Hopefully this will help you help me!

---

### Post by Yellow Pasque on 2010-01-03
Copy and rename one of your mp3's to test.mp3 so it doesn't have any strange characters in it. Then, try the gst-launch command again:
```
cd ~/Music
cp *SOMEMP3* test.mp3
```

---

### Post by Aldentron on 2010-01-03
This appeared to work, thank you.  I'm assuming all I needed was the gstreamer thing.
 
There is still no sound coming through the audio jack, I have come home now and tried plugging in my sound system into it and no sound was produced, the same result as plugging ear buds into it.  When I used Ubuntu (I believe the version was 8.10,) I could plug any kind of speakers in and it would work fine.  Like I said earlier, I went into alsamixer and turned all the levels to their maximum and made sure none of them were muted. Any ideas?

---

