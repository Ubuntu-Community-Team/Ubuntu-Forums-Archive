---
title: "Audio codec 'Windows Media Audio v3' is not handled."
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by bruban on 2007-11-28
I'm trying to listen to a new .wma file.

I have the ubuntu-restricted-extras installed under Ubuntu 7.10 i386.

I can play the file under WinXP.

I can listen to other .wma files on this system.

Any ideas?

- I get the following message in Totem Movie Player:

> Audio codec 'Windows Media Audio v3' is not handled.

- gxine 0.5.11 opens the file but does nothing.

- mplayer gives the error message:

> Cannot find audio format 0x162.

- vlc pretends to play the file, but no sound.

---

### Post by Jenda on 2008-04-07
I have the same problem... any solutions found so far?

---

### Post by bruban on 2008-04-07
No not yet.

I understand that this is a newer version of the .wma format.

I'm waiting for the new version of Ubuntu and will try it again then.

---

### Post by ubuntu-freak on 2008-04-07
Have you installed the gstreamer0.10-pitfdll package? It's included in the Hardy version of restricted-extras, but has been available to Gutsy users to install seperately. Also, did it not play in MPlayer/VLC even with the w32codecs package installed?
 
Nathan

---

### Post by cor2y on 2008-04-07
Yeah for any of the newer windows media codecs, aka wma3, or the new hidef vc-1 video codec you will have to "cheat" and install the w32codecs , so far as far as i can tell totem with both the gstreamer or xine backend cannot play these files.
I have not tried to run any of the newer files on gstreamer with the pitfdll plugin so i don't know if that works but mplayer with the w32codecs installed will play the files in question.

---

### Post by bruban on 2008-04-07
Thanks for your help reassuringlyoffensive and cor2y.

I can't find the w32codecs package using synaptic.

I have universe, multiverse and restricted repositories enabled.


I'd check the gstreamer0.10-pitfdll but I have a temporary problem with my sound playback at the moment. It stopped working after a recent system update and I haven't been able to get it back up and running. I have a separate forum post on this. I'll check when I have this resolved.

---

### Post by kostkon on 2008-04-07
> **bruban said:**
> Thanks for your help reassuringlyoffensive and cor2y.

I can't find the w32codecs package using synaptic.

I have universe, multiverse and restricted repositories enabled.


I'd check the gstreamer0.10-pitfdll but I have a temporary problem with my sound playback at the moment. It stopped working after a recent system update and I haven't been able to get it back up and running. I have a separate forum post on this. I'll check when I have this resolved.

You have to add the [*Medibuntu*]("http://medibuntu.org/") repository in your software sources list in order to be able to install the *w32codecs* package. Instructions on how to do it you can find [here]("http://help.ubuntu.com/community/Medibuntu").

Also, you'll need the *gstreamer0.10-pitfdll*, as someone suggested above. This will give *Gstreamer* the ability to use these Windows codecs.

---

### Post by ubuntu-freak on 2008-04-08
Sorry bruban, I presumed you knew about the Medibuntu repo. Check out my [how-to](http://ubuntuforums.org/showthread.php?t=661833) for help with other multimedia issues, such as streaming, converting sound/video and DVD playback/ripping/burning.
 
Nathan

---

