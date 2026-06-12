---
title: "Audacity not playing"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by Eminem on 2007-08-03
When trying to play back the stuff I got in my workspace or whatever you call it by playing the play button, I get "Error while opening sound device. Please check the output device settings and the project sample rate."

Any help? Possibly any drivers I'm missing? Any packages? Anything?

---

### Post by obiwan on 2007-08-03
quit banshee, amarok, or whatever music player you use. Run audacity and in Edit -> Preferences you can choose de output device (I have /dev/dsp).

---

### Post by Palmyra on 2007-10-28
Here's what I found through a Google search:

Try opening Audacity as SUDO, using the following command:

gksudo aoss audacity

Explanation:  This opens Audacity using administrative priviliges, using AOSS (I am thinking this is OSS).  Anyhow, give it a try.  If you're having problems with GKSUDO, use SUDO (even though it's not recommended).  If it complains about AOSS, I guess you have to download and install it (use Synaptic or use sudo apt-get install aoss). 

I know it's silly to open Audacity using SUDO, but it worked for me.

---

