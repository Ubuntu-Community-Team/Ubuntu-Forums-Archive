---
title: "Amarok acting weird since last kernel update"
date: 2009-07-13
forum: Multimedia Software
---

### Post by eponymous on 2009-07-13
Ubuntu Jaunty 64 bit, latest amarok, using ALSA

Everything was peachy with ALSA and Amarok, had audio from multiple apps at once, no problems.

I *think* this started after the recent kernel update. Amarok will add a random track from my collection to the end of the playlist when I add files to the list, and when a track ends and it goes to the next track. I also can no longer play audio from 2 sources at once.

Has anybody else experienced this? What should I try?

All I've done so far is to remove amarok with --purge and reinstall. I'm not really looking forward to monkeying with ALSA or going to Pulseaudio as I've had trouble with them in the past, I think mostly related to my sound card (m-audio audiophile 2496).

Thanks in advance!

---

### Post by igorzwx on 2009-07-13
They are changing everything everyday, trying to fix Pulse

It should be possible to fix your playback by editing /etc/asound.conf

try make alsa default

[http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html](http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html)

---

### Post by eponymous on 2009-07-13
> **igorzwx said:**
> They are changing everything everyday, trying to fix Pulse

It should be possible to fix your playback by editing /etc/asound.conf

try make alsa default

[http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html](http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html)

Thanks this looks promising. i'll give it a try after work and post the results.

I don't expect this will address the random files being appended to the playlist though...that one has me totally stumped.

---

### Post by igorzwx on 2009-07-13
This may help too:

[http://ubuntuforums.org/showthread.php?t=1211713](http://ubuntuforums.org/showthread.php?t=1211713)
 				 				**[SOLVED] Re: constant beeping noise (impossible to turn off)** 			
 			 			 		   		 		 		I just got it all working with soundcheck's script :grin::

[http://ubuntuforums.org/showthread.p...10#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")
 		                   		  		  		  		  		 		 			 				 				* 					 						Last edited by manualqr; 26 Minutes Ago at 07:08 PM.. 					 					 						Reason: [solved] 					 				*

---

### Post by eponymous on 2009-07-26
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

this is what worked

symptoms: amarok wouldn't allow multiple sound streams, video playback was extremely sluggish with amarok running

ran that script and rebooted now everything's fine

---

