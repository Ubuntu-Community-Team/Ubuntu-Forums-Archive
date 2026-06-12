---
title: "I've been unable to capture sound since Gutsy"
date: 2009-05-31
forum: Multimedia Software
---

### Post by david.rahrer on 2009-05-31
I realize this is a nebulous question but it's out of frustration and the lateness of the hour.  Is there any chance that I will ever again be able to record audio captured from the system (i.e., what's playing through the speakers) onto something like the gnome sound recorder?  I would throw in Audacity but let's keep it simple for now.  This fairly simply task has eluded me since Gusty, and I skipped intrepid entirely hoping for an answer in Jaunty.  

From what I can tell, all my other audio features work well, except for intermittent crackling mainly of IM notifications (separate issue).  After trying multiple tutorials on earlier setups, I have this one OEM default.  

I'll add any hardware or other information requested tomorrow (I'm really about to fall over), but I would really, deeply appreciate some assistance.  I need to do this now and then and it becomes an issue each time I can't.  I found myself checking out Debian and even Fedora tonight and that's just nuts that an issue has existed in three versions and could cause someone to dump such a fantastic distro after 3 years.  

I'm  just desperate here and will work with anyone who thinks they know how to fix it.  If this is known to be hardware related, I'll get a new sound card.  Thanks for any help.

Jaunty i386_32
hardware specs as needed tomorrow.

Goodnight,

---

### Post by ajgreeny on 2009-05-31
I can certainly do it with both audacity and sound recorder.  You will need to open your volume control and make sure that in the preferences of that the "Mix" track is available and set to correct level, and that the "Capture" track is also enabled and set correctly.  Perhaps different sound cards do not offer the same options as mine, but if that does not work, I don't know what else to suggest.

---

### Post by jjross on 2009-05-31
What I had to do was open Applications/Sound&Video/PulseAudio Volume Control, open the recording tab, then open whatever you are wanting to use for recording and start it, then look on the recording tab in the PulseAudio Volume control and see if there is any activity showing, if there is, right click on the device listed and it should give you a choice of streams to choose from, then choose a stream (probably different than the one already marked) and try it.
I found this here, [https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")
Hope this helps, it fixed my problem.

---

### Post by david.rahrer on 2009-05-31
> **jjross said:**
> What I had to do was open Applications/Sound&Video/PulseAudio Volume Control, open the recording tab, then open whatever you are wanting to use for recording and start it, then look on the recording tab in the PulseAudio Volume control and see if there is any activity showing, if there is, right click on the device listed and it should give you a choice of streams to choose from, then choose a stream (probably different than the one already marked) and try it.
I found this here, [https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")
Hope this helps, it fixed my problem.
Thank you both for the prompt response -- jjross, I owe you a beer, you nailed it!  I had a video tuner card installed and the stream was defaulting to the audio section of that.  I changed it for sound recorder and Audacity and both work perfectly.  I'm so grateful, thank you.  

I had done so much troubleshooting in Hardy that I guess the tutorials just weren't sinking in anymore.

---

