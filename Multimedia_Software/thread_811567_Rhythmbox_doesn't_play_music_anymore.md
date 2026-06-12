---
title: "Rhythmbox doesn't play music anymore"
date: 2008-05-29
forum: Multimedia Software
---

### Post by GuidoDavid on 2008-05-29
Greetings.

Since the last two weeks or so Rhythmbox has been behaving weirdly. It crashes in the middle of a song, produces no sound and refuses to play any other thing. If you insist, it will shut down. Those events were annoying but scarce, but this morning, when I woke up, there was no music, and when I restarted Rhythmbox, it wouldn't play anything at all. Or, after restarting, would play a song and nothing more.

I started Rhythmbox from the terminal, when it loads the library, the terminal displays this message:

> Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/x-rar decoder|decoder-application/x-rar
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/x-rar decoder|decoder-application/x-rar (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing

But I am not sure if this is the problem at all. I do not think so.
After this message, sometimes I could play music again, for a short while, sometimes I couldn't. When the player became stuck, I always got the following message:

> (rhythmbox:28222): GStreamer-WARNING **: loop detected in the graph of bin bin10!!

(rhythmbox:28222): GStreamer-WARNING **: loop detected in the graph of bin bin14!!


I googled for it and did not find anything useful. Rhythmbox is back again, after half an hour silent. But I want to know why, I want to correct the problem and avoid it.

Thanks in advance.

---

### Post by GuidoDavid on 2008-05-30
This morning I woke up and the sound was choppy, but the songs played normally when I stopped the player and pressed Play again.

I am using Hardy with the latest updates on an Dell Inspiron 1520.

---

### Post by GuidoDavid on 2008-06-06
Now the problem is even worse. Now it does not play anything at all, after trying several times.

*Please* could anybody help me? I am a total newbie, just dropped Windows totally, so I really would appreciate some help.

---

### Post by xc3RnbFO8P on 2008-06-06
Do you dual boot?

---

### Post by GuidoDavid on 2008-06-07
My hard drive is a mess.

Two 20 gigs partition, another one, 80 gigs.

I dual boot two installs of Hardy, but I only use one. The new one is never used, some day I will get AptOnCD and install everything and configure it neatly and painlessly, unlike this.

Windows partition and Dell Media Direct are now gone.

---

### Post by forger on 2008-06-07
I would do the following:
1) close rhythmbox and any window or application related to music and sound. Open up gnome terminal
2) clear the settings - **[COLOR="Red"]WARNING![/COLOR]** It practically removes your rhythmbox playlists and cached library files, you will have to reset those manually
```
rm -rf .gnome2/rhythmbox/
```
3) reinstall rhythmbox
```
sudo apt-get install --reinstall rhythmbox
```
4) check/reinstall if you have the necessary codecs
```
sudo apt-get install --reinstall lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x
```
5) reboot your machine
6) Run rhythmbox - fix up your media library and try to play a file

---

### Post by GuidoDavid on 2008-06-07
Thank you very much for the help.

I did everything you advised, yet, when I start Rhythmbox from the console, get the same message about the missing plugin and still it blocks occasionally.

Concerning the other error message, I have not see it again.

Again, thank you very much.

---

### Post by Pjotr123 on 2008-06-07
Try this:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and then this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

That should do the job, I think. :-)

---

### Post by forger on 2008-06-08
hey, maybe it's not a sound file, maybe it's a compressed rar archive?
try rename to .rar and right-click on it, select "extract here"

---

### Post by GuidoDavid on 2008-06-08
I erased some .rar files that were on my Music folder (even if they did not show on the library).
The message disappeared and it seems I have no more trouble with weird hangs of rhythmbox. I checked and it seems I have all the codecs, except the JDK, just installing it as I write this.

Let's hope it keeps this way.

Thank you very, very much, people!

---

