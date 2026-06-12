---
title: "Microphone flakiness, audio mixer settings lost, unable to Skype, etc."
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by monocongo on 2007-02-27
I am trying to configure my headset microphone to work reliably so I can use Skype.  I was successful with this yesterday but today I tried using Skype again and the microphone is no longer working.  I opened the mixer (KMix) and the settings appeared to have been changed.  I monkeyed around with the KMix settings (as well as the settings of alsamixer, which affects the same audio settings I think) and now I can at least hear my voice when I talk through the microphone.  However Skype never records my voice when I try the Skype test call, and when I try to record a test audio file using the Sound Recorder application it hangs on me (never recording anything, and I have to kill the app).  After modifying the audio settings (I'm not sure which ones or whether it was through KMix or alsamixer that caused this) Skype would not open without error and I had to destroy the ~/.Skype directory in order to get Skype to come up again.

Here are my settings in KMix:

Output: all settings are turned on
Input: none muted, Mic, IEC958 Playback, and Capture turned on
Switches: Mic Boost, IEC958, Duplicate Front, and External Amplifier turned on
Surround Jack Mode: Shared
Mic Select: Mic2
IEC958 Playback Source: PCM
Channel Mode: 2ch
At the bottom of the KMix window it says ATI IXP (my sound card info?)

I really don't have a clue as to how these settings should be configured, but I'm pretty sure that these are what I had yesterday when I had it working the first time.  Since then I tried to hibernate the machine, and that didn't really work so I did a hard power down (since it was stuck on a black screen with a single blinking cursor after the hibernate).  It booted up fresh today with no troubles, and later in the day I noticed this recurring microphone problem.  Maybe the incomplete hibernate and ungraceful power down did something to the sound card settings?

Any suggestions or ideas will be greatly appreciated, thanks in advance for your help.

---

### Post by monocongo on 2007-02-27
It seems like I'm not the only one with these issues, according to this Skype forum  **[thread]("http://forum.skype.com/index.php?showtopic=66544")**.

What seems to have solved my troubles for now is that I started Skype as root:
```
sudo artsdsp -m skype
```

After doing that and testing that Skype can record using the microphone settings I quit Skype and started it again normally (i.e. as me and not as superuser) and I could still use the microphone.  Hopefully the relevant mixer and Skype settings will stick and I won't have to go through this process again.

---

### Post by MissG on 2007-08-20
i got it working using the thread you linked to, thanks. (i did the terminal method)

---

### Post by fallingleaf on 2007-08-27
Thanks monocongo (there are howler monkeys that come around my house at least once a week).

One thing I'd like to point out for people using Ubuntu instead of Kubuntu is that the gnome mixer (the thing that comes up when you right click the little speaker on the panel and select "open volume control") is pretty useless.  I tried and tried to get things to work changing settings on that.  If people want to use a GUI they should probably install kmix.  Otherwise alsamixer is actually like a GUI only you can't use your mouse.  If anyone knows of a good mixer for Gnome, I'd love to hear about it.

Edit: I found a good mixer in another thread.  Enable universe repositories:
```
sudo aptitude install gnome-alsamixer
```

---

