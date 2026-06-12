---
title: "Volume Control Stopped working in Edgy"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by Xhosa on 2006-11-30
I upgraded from Dapper to Edgy about a week ago, and the sound on the system kept working happily.

After a reboot today the gnome-volume-control icon shows 'mute' and clicking on it returns:

No volume control GStreamer plugins and/or devices found.

Sound is working otherwise (System->Prefs->Sound and mpg321 both work).

User account is in audio group.

I have done a reinstall of gnome-media and ALL gstreamer packages that gnome-media depends on.

Any ideas why this doesn't work?

---

### Post by polly1 on 2006-11-30
Hi 

I had a similar problem with my Audiology Sound card with 4 speakers and got around it by checking all my sound settings using "alsamixer". The "surround" had changed to 0 for some reason. When I adjusted it to 100 my sound was ok again.

Type "alsamixer" command in your terminal and check the settings, because this may be the problem.

---

### Post by Xhosa on 2006-12-01
Thanks, but no joy.  Alsa Mixer settings are all fine, and the alsa mixer adjusts volume/balance etc quite happily - its just the gnome-volume-contorl applet that seems unhappy. 

Any more suggestions appreciated.

---

### Post by TZRick on 2007-02-02
> **polly1 said:**
> Hi 

I had a similar problem with my Audiology Sound card with 4 speakers and got around it by checking all my sound settings using "alsamixer". The "surround" had changed to 0 for some reason. When I adjusted it to 100 my sound was ok again.

Type "alsamixer" command in your terminal and check the settings, because this may be the problem.

Awesome! Thank you! I did as you said and adjusted the various controls in the terminal interface and now I can control my sound!

FYI: SoundBlaster Live! Value Digital, Pinnacle PCTV Pro PCI TV/Radio/Video Capture card.

---

