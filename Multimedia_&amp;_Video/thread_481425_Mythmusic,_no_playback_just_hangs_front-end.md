---
title: "Mythmusic, no playback just hangs front-end"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by EmuMannen on 2007-06-22
Just installed mythtv under 7.04 Feisty (AMD64 on an abit NF-M2 mobo) following the Ubuntu “[Combined Backend Frontend]("https://help.ubuntu.com/community/MythTV_Dapper_Backend_Frontend")” guide. Everything is working great (tv, video etc.) except mythmusic. I import my music (mainly MP3 and OGG files) but the front-end hangs when I try to play anything using mythmusic. I also tried to play a CD, it didn’t play but it didn’t hang the front-end either. I got sound watching TV and playing video (trough mythvideo).

---

### Post by EmuMannen on 2007-06-22
Found the solution myself (on another [forum]("http://www.mythtvtalk.com/forum/viewtopic.php?t=4690")):
> 
Hi,

I had the same problem; did you setup the audio output device for MythMusic?

The default setting 'default' will not work, it must be set for example to 'ALSA:default' or whatever suits your setup.

Cheers,
J


---

### Post by superm1 on 2007-06-22
Hi,
Was there anything else to this problem?  If the only thing was setting the music device to be ALSA:default rather than default, please file a bug on launchpad.net.  We'll be sure that the default when mythmusic is setup is switched over to be ALSA:default.

---

### Post by EmuMannen on 2007-06-23
> **superm1 said:**
> Hi,
Was there anything else to this problem?  If the only thing was setting the music device to be ALSA:default rather than default, please file a bug on launchpad.net.  We'll be sure that the default when mythmusic is setup is switched over to be ALSA:default.
Maybe it works if English language is selected (default configuration="default") but I was running with Swedish language and the default setting was then "Förvald" (default in Swedish), no wonder Myth got into trouble if it was looking for a sound device named "Förvald"! ;)

I will file a bug if anyone could point me in the right direction (haven't filed a bug report for Ubuntu before). Thanks in advance...

---

### Post by superm1 on 2007-06-23
That indeed can be trouble :) 

So the box had Förvald previously, and ALSA:default worked.  Can you try just "default" and see what happens?  You might have hit a different bug then I was expecting (this appears to be something that shouldn't be translated), and this might need to be submitted to upstream.

---

