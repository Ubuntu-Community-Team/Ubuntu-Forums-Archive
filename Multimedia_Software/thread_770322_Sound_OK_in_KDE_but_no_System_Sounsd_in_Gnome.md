---
title: "Sound OK in KDE but no System Sounsd in Gnome"
date: 2008-04-27
forum: Multimedia Software
---

### Post by pieronip on 2008-04-27
Hi

I have gone through the Sound Problems sticky and all is as it should be with my M-Audio 2496 card.

In Gnome, CDs, DVDs, WAV files play fine but system sounds will not play even if a select a different (non-standard) WAV file.

In Sound Preferences (Gnome), Autodetect of sound device does not work and I have to select ICE1712 multi as the correct device.  If I do this, 'test'produces a tone. Selecting ALSA also works but OSS and PulseAudio do not, they produce an error as follows:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink:Failed to connect stream: Invalid argument!"

The strange thing is that the test in sound preferences works for Sound Events but the real thing doesn't!

Everything seems perfect in KDE however!

As you might surmise, Gnome is my preferred desktop so the fact that KDE works is a bit irritating!

Any suggestions?

Thanks.

---

### Post by pieronip on 2008-04-29
It looks unlikey that I will get an answer to this as the forum is swamped with sound problems.

So let me ask a slightly different question.

Where can I read good documentation on Ubuntu sound so I might have some hope of resolving this myself?

Thanks.

---

### Post by fede on 2008-05-05
I have the same card and the same problem myself. Actually, I hadn't noticed that there were no system sounds... since I find them irritating I usually turn everything off. 

In any case, perhaps you haven't still seen the related bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442) ?

People talk about a workaround in the bug report, but the link is dead. Hope it is temporary. Good luck, and please post if you find out anything!

---

