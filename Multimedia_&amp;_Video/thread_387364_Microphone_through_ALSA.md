---
title: "Microphone through ALSA ?"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by Dekunuts on 2007-03-18
Hi, my Ubuntu installation (only OS/PC I have) has been working great for over a year, but there is one problem that remains. My microphone does not work very well. I can get  it to work under OSS but then I do not have a mic boost option available and the audio is very silent. I can see ALSA has a mic boost option, but my microphone is the only thing that does not want to work with alsa. When I go to system -> Preferences -> Sound both options under the 'Audio Conferencing' tab need to have OSS enabled for my microphone to work. If i try ALSA sound playback, the test works, but when i choose alsa for sound capture, i get the following error : 

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink ! profile=chat: could not open resource for writing.

Can anyne tell me how to use my microphone through ALSA, or propose a different solution in case I'm not getting it. I have already tried reinstalling the audio related packages as said in audio guides, but that does not work. Also, it's a normal microphone, not USB.

---

### Post by garybrlow on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Its a long standing ALSA bug. I myself have no mic/sound capture/recording capabilities as of the moment. Please Read, Review, Confirm the bug and related info  herehttps://bugs.launchpad.net/ubuntu/+bug/80531. Don't forget to register at launchpad.net if you already haven't done so to post/confirm bugs there.

Cheers!!!


GaryBrlow :biggrin:

---

