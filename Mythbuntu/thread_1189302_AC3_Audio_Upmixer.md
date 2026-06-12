---
title: "AC3 Audio Upmixer"
date: 2009-06-16
forum: Mythbuntu
---

### Post by xinix on 2009-06-16
So I was looking through the setup options (simply out of geeky curiosity) and I noticed that "AC3 audio upmixer" has been added to the audio options.  This is really great and now my audio receiver is telling me that the audio is being sent as a digital 3/2/1 signal. :D It's still glorified stereo since the TV signal is only in stereo (no digital for me), but it sounds nicer in my opinion.

One thing is that the audio level in the recordings settings needs to be less than 100%.  At least on my system I get crackly metallic clipping.  If I set it to 95% then it's not a problem.
The problem is that I have a bunch of old recordings that have the audio level set to 100%.  So playing these with the new upmixer is not pleasant.  Luckily "Ctrl+U" toggles the upmixer off/on while you are watching the recording/live tv; and turning it off fixes the crackly noise issue.

My question,  is it possible to set the upmixer to "toggled off" by default so that it can be turned on manually for new recordings?

---

### Post by robertrej on 2009-06-19
I was just wondering when your system displays ac3 5.1
are you running a ac3 5.1 sound track or an ac3 2 channel
stereo sound track? I have a lot of ac3 stereo tracks
and like the sound quality . I can convert ac3 stereo
to ac3 5.1 but it requires a lot of work.I am using ubuntu
8.10 and may move to 9.04 if that audio feature will do
what I want.Not as answer to your question but I may find one
soon.

                         Thanks very much
                         Bob

---

### Post by xinix on 2009-06-19
If I'm playing a dvd/file with a 5.1 track then the sound is 5.1; but this was the case without any upmixing.  What the AC3 upmixer is doing is converting (upmixing) the 2 channel stereo track from the tv broadcast into something that my receiver thinks is 5.1.  It sounds better in my opinion.
This feature is a patch to mythtv itself so you'd have to use mythtv to play your tracks.  I'm using the Avernard patched repo's with Ubuntu 8.10.  There really isn't much documentation that I can find about this feature. There may be ways to do this outside of Mythtv, but I don't know.

---

