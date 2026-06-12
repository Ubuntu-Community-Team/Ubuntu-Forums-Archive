---
title: "No sound, new install"
date: 2011-01-16
forum: Mythbuntu
---

### Post by Twig E. Pottox on 2011-01-16
New mythbuntu fresh install on dual boot/HDD setup with win 7. Using Mobo sound, audio tests ok on speakers and can play streams through browser. But nothing on Mythbuntu.
under setup>Audio system> device is alsa default, speakers config: stereo
Audio mixer is alsa default. 

absolutely no sound on myth,  Live TV and DVDs play but silent. at first there was a volume control slider that showed when trying to adjust volume on the keyboard. but that has disappeared.  

any magic switches hidden somewhere?  Thanks in advance for your help.

---

### Post by nickrout on 2011-01-16
> **Twig E. Pottox said:**
> New mythbuntu fresh install on dual boot/HDD setup with win 7. Using Mobo sound, audio tests ok on speakers and can play streams through browser. But nothing on Mythbuntu.
under setup>Audio system> device is alsa default, speakers config: stereo
Audio mixer is alsa default. 

absolutely no sound on myth,  Live TV and DVDs play but silent. at first there was a volume control slider that showed when trying to adjust volume on the keyboard. but that has disappeared.  

any magic switches hidden somewhere?  Thanks in advance for your help.

Firstly is audio being captured in your recordings? Use ffmpeg or mediainfo to check. Try playing one via mplayer or something else you know works.

Secondly have you scanned for audio devices in the frontend setup? (Assuming you are using 0.24).

---

### Post by Nobodyspeshul on 2011-01-17
If you haven't already, check your alsamixer settings and make sure everything is turned up and not muted.

---

### Post by nickrout on 2011-01-17
> **Nobodyspeshul said:**
> If you haven't already, check your alsamixer settings and make sure everything is turned up and not muted.

worth looking at but twiggy tells us the audio is working outside myth (at least thats my interpretation of what he is saying)

---

### Post by Twig E. Pottox on 2011-01-17
> **nickrout said:**
> worth looking at but twiggy tells us the audio is working outside myth (at least thats my interpretation of what he is saying)
Thank you both for answering my request.  Indeed nickrout, you interpret my Midwestern twang correctly,  the audio is working outside of Myth both in the speaker test and streaming radio/audio thru Firefox.  

However I went back for a second visit to the settings within myth and the system audio settings, if anything wasn't set  at 100 it is now. and now I have audio on live TV & waiting for a recording to finish to check.  

The audio is not exactly loud as compared to other inputs but serviceable, Guess I'll continue tweaking...

Not exactly sure what you mean by "scan for audio devices in the front end setup".  where do I find this scan option?

Thanks again for your help

---

### Post by nickrout on 2011-01-17
> **Twig E. Pottox said:**
> 

Not exactly sure what you mean by "scan for audio devices in the front end setup".  where do I find this scan option?

Thanks again for your help

It's only in 0.24, but it's Setup menu|General|Page 3 or 4 - theres a button at the top of the page "Scan for audio devices"

---

### Post by Twig E. Pottox on 2011-01-18
Thanks again for your response. Sorry, I should have mentioned the release I'm using, 0.23 stock 10.10 fresh/new install.  Still setting up the BE/FE , haven't even tried a client yet.  Other issues first. Again, appreciate the help. ---  I'd put a big ol' [COLOR="Black"]**SOLVED**[/COLOR] on this thread if I knew how its done in this forum.

---

