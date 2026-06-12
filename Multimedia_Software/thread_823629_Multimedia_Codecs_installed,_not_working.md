---
title: "Multimedia Codecs installed, not working"
date: 2008-06-09
forum: Multimedia Software
---

### Post by ProspectorJoe on 2008-06-09
I am sure I have all of the codecs I need to play music. I went into synaptic, searched GStreamer and all of the ones for Alsa and PulseRadio were installed and what not, but whenever I go into Totem or Rhythmbox or anything else, if I click on the song I want to play it just doesn't do anything or freezes and I have no idea why.

Audio does work, I can work flash fine, and I have no idea how to fix this. Thanks.

---

### Post by cozmicharlie on 2008-06-09
Sounds like you have a good start but still may be missing something.  Some more info will help:  
what version of Ubuntu are you using?
What type of files are you trying to play (mp3 or??)
Have you installed the Ubuntu Restricted Extras?  If you have not done this I would try this first - install from Synaptic.  Try and play your files again and if they still don't play post back with the above info and we can start trouble shooting.

---

### Post by Pjotr123 on 2008-06-09
Apply this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and then this one:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

That should do the job.  :)

---

### Post by ProspectorJoe on 2008-06-09
I am using Ubuntu 8.04, and it's any type of audio file be it .mp3 or .flac etc.

Movie files also do not work. They were working on Saturday, I know I watched a .avi file on saturday, but today, nothing.

And yes I have the Ubuntu Restricted Extras installed so that's not the problem, unfortunately.

---

### Post by cozmicharlie on 2008-06-09
> **ProspectorJoe said:**
> Movie files also do not work. They were working on Saturday, I know I watched a .avi file on saturday, but today, nothing.



Did you do an upgrade or install something that might cause a change?

I believe this is the best How To in the forums on Multimedia ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)) - you may want to read through this and see if maybe there is something you missed.

---

### Post by cozmicharlie on 2008-06-09
One more question - do your music file names have any blank spaces in them?

---

### Post by cozmicharlie on 2008-06-09
One more item to try.  I have read that some people are having problems with Pulse Audio in Rythmbox so you may want to play with your settings.  Go System>Preferences>sound audio playback should be set to default.  Change it to Alsa and see if that helps.

---

### Post by Yellow Pasque on 2008-06-09
What sound card do you have? (lspci | grep dio)
If it's an HD Audio compliant codec, see this: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
You might also try OSS4 (link in sig)

---

### Post by ProspectorJoe on 2008-06-09
Hmm. Well, I got the audio working, so thank you for that.

For some reason it still will not play in certain players like Amarok and Rhythmbox, but I just deleted those and installed listen music player which I guess will work for the most part, so thanks for the help!

---

### Post by Yellow Pasque on 2008-06-09
Go to System -> Preferences -> Sound 
What do you have those set as?

---

