---
title: "VLC mp3 glitches on first secnds of playback"
date: 2010-08-08
forum: Multimedia Software
---

### Post by FreedomOverdose on 2010-08-08
Hello

On almost each mp3 file I try to play, VLC will "lag" during the first seconds. There may be some screeching noise. It looks like vlc can't keep up with the bitrate, and it "skips" some bits. 

This doesn't happen with totem (the default media player). Any ideas?

tia :)

---

### Post by FreedomOverdose on 2010-08-09
anyone please? I'd really like to use VLC, but this is really annoying... :(

---

### Post by FreedomOverdose on 2010-08-14
anyone pls? :(

---

### Post by FreedomOverdose on 2010-08-22
hmm looks like some cache issue. it happens only the first time when I play a file, its ok the second+ time

---

### Post by FreedomOverdose on 2010-08-26
now this is also happening on my pc, and on my laptop, so it should be a general problem.. :(
cmon ppl :(

---

### Post by wolfdale on 2010-08-30
I have also noticed that VLC will also sound glitch on mp4 videos during startup however Gnome movie player will start without any sound glitches. I played around with cache sizes and drop frame rates cannot get rid of the glitch. The glitch is more pronounce when switching from video to video.

---

### Post by FreedomOverdose on 2010-08-30
> **wolfdale said:**
> I have also noticed that VLC will also sound glitch on mp4 videos during startup however Gnome movie player will start without any sound glitches. I played around with cache sizes and drop frame rates cannot get rid of the glitch. The glitch is more pronounce when switching from video to video.
so it's definitely cache... anyhow, the latest version of vlc isn't on the repos, so we have to wait for maverick to test it with the latest vlc

---

### Post by luigi_mb on 2010-08-30
Actually there is a new PPA for vlc, and it carries v1.1.4. See

[http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html#more](http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html#more)

I added the PPA and then upgraded my vlc to v1.1.4.

I don't know if this peculiar to my Lucid installation, but when I used Synaptic to upgrade vlc there was an error about vlc itself and vlc-plugin-notify. However a second call to Synaptic corrected the problem. It works perfectly well.


/luigi

---

### Post by andrew.46 on 2010-08-30
Hi FreedomOverdose,

I will admit that I build my own vlc under Lucid Lynx but I have not ever experienced this issue. In fact I have just tested it now by switching from file to file, both mp3s and mp4s with varying codecs, all ran flawlessly throughout and in particular there were no sound glitches on startup. I assume you are using the repository vlc?

Andrew

---

### Post by roddie on 2010-09-22
I've upgraded to VLC 1.1.4 and am still having the same problem.

---

### Post by Claus7 on 2010-10-08
Hello,

have the same problem. The sound is getting better, while the file plays though till it seems to be fine. Such a mysterious bug!

Version of vlc as mentioned, tested on avi files, maverick.

edit: same problem with kaffeine, no problem with mplayer

edit2: after a fresh install of a 64bit version of maverick, vlc's problem vanished

Regards!

---

### Post by kriukov on 2010-12-04
I have exactly the same problem with VLC on 10.04. I had a [similar problem]("http://ubuntuforums.org/showthread.php?t=842875") on 8.04 and it was solved by changing the output modules. Any suggestions about the current problem?

---

### Post by kriukov on 2011-01-22
Bump...

---

### Post by satosh on 2011-08-08
This happens with me too.
VLC 1.1.9 on Natty 64 bit.

When next track on playlist is starting, there are two or three glitches before it runs smoothly. 

Have only tried with music so far but seems I always have to adjust audio by about -250ms to get in sync when watching movies.

Have tried changing the output modules with no luck.

---

### Post by mc4man on 2011-08-08
Yuo can try either of the 2 methods mentioned here. (for both stutter and de-sync

I prefer the latter, using alsa instead of pulse. To do so properly you must change the output module AND specify the device.
[http://ubuntuforums.org/showthread.php?p=11126930#post11126930](http://ubuntuforums.org/showthread.php?p=11126930#post11126930)

---

### Post by satosh on 2011-08-09
Thanks! Seems to fix the glitches.

Although alsamixer gives me "this sound device does not have any controls". But I get by.

Again, thank you!

---

### Post by kriukov on 2012-03-05
Finally solved - by upgrading to VLC to 1.1.13 from a third-party repository.

---

