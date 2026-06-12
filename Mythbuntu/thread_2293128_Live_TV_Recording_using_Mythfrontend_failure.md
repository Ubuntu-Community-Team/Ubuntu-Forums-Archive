---
title: "Live TV Recording using Mythfrontend: failure"
date: 2015-09-02
forum: Mythbuntu
---

### Post by Antonio_Carballo on 2015-09-02
OK. This problem is driving me insane. I go to Mythfrontend on my MAC and start watching a channel. I press S to get the guide and then select to record it. So far great until I go to the recording and click on the show that it's supposed to be recording and I get: *This **showing will not be recorded because this rule does not match any **showings *[I]in the current program listings"

I delete the recording rule. I go to Kodi and run the plugin for MythTV. I watch the channel and select to record it. It records it!

Q: Why is the Mythfrontend not recording the live show? A mystery to me so far.

Any help will be greatly appreciated.

/AC

[/I]

---

### Post by aelfric55 on 2015-09-03
If you're watching livetv and you suddenly decide to record the program  that's on the screen now, you'd normally just press "r". A second "r" press toggles livetv recording back off. The recording file is actually begun from when you begin watching the program, not from when you toggle "r". If livetv recording is toggled on with "r" and you watch through, say 5 programs on one channel in your livetv sitting (a minor miracle itself without livetv crashing in the current iterations of mythfrontend), these 5 will end up properly divided into individual files with correct metadata in Watch Recordings.  

On the other hand,  "s" brings up the EPG guide, where you'd normally schedule the recording of episodes/shows after the one currently on the screen.

---

### Post by Antonio_Carballo on 2015-09-04
I see my mistake. In Kodi the record option is equivalent of pressing "r" in the Mythfrontend while watching the program live. I tested what you said and you are right: Pressing "r" will record the program but using the Guide to record the currently tuned program will schedule it but not record it.

Thanks for the feedback!

/AC

---

