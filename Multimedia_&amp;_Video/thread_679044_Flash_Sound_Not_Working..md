---
title: "Flash Sound Not Working."
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by jkzubu on 2008-01-26
I am running Ubuntu 7.10, AMD64-bit version and I am using Pulse Audio. My sound card is an Audigy SoundBlaster SE.  This morning I installed the flash fix: flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb, as described in this post: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397).  

This fix seems to have gotten the video portion of flash to work, but there is no audio for the videos in: Youtube, Yahoo and a few other websites I tested.  Also, my audio for the login screen (bongo drums) no longer functions.  The rest of my audio works beautifully: music in Audacious, Exaile, Rythmbox, even the system sounds (clicks, beeps, boings, etc.).  Prior to installing this fix, flash would rarely work perfecly (with sound), would sometimes partially work, but mostly would never work. Especially, yahoo videos would never work.  The flash fix seems to be working ok for video, but there is no audio.

I found this code:  
mv ~/.asoundrc .asoundrc.old
mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
in post #4 of this thread: [http://ubuntuforums.org/showthread.php?t=590989&highlight=firefox+pulse+audio](http://ubuntuforums.org/showthread.php?t=590989&highlight=firefox+pulse+audio)
and ran it in a terminal.  

After a restart, all of my audio (and video) worked perfectly in flash videos (Youtube, Yahoo, etc.), but the rest of my audio stopped working (couldnt find the audio source or something).  I was able to reset the audio using asoundconf, but now the audio portion of the flash videos is gone again (video still working) and the rest of my audio is back working to the way I described it above.  I understand that there are known bugs with Flash and AMD64-bit, but I also know that all of the sound will work.  It just appears that all of the sound will not work together...yet.

Can someone please answer the following:
What exactly are the mv scripts above doing?
Why do these scripts activate the flash audio and deactivate the other audio (for music and etc).
How can I get all of the sound to play nice together and make everything work?

Thank you.

JK

---

### Post by Metaljaz on 2008-01-26
Follow the below thread:

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

---

