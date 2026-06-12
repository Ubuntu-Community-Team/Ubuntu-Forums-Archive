---
title: "Audigy 2 ZS Multichannel Playback Problem"
date: 2009-09-12
forum: Multimedia Software
---

### Post by dreamkin on 2009-09-12
I have a Soundblaster Audigy 2 ZS hooked to a 7.1 speaker setup. 

While the sound quality I get is great, it seems to be impossible for me to run two applications with sound output at the same time.

Let me elaborate:

The driver I am using for "Music and Movies - Sound Playback" is "Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) Multichannel Playback (ALSA) since only this driver seems to be giving me Surround Sound (that is: Mixer controls for all channels work and I am able to obtain surround stereo sound coming from all speakers)

The problem is that two applications using the same driver cannot run. Meaning I cannot run 2 movies at the same time. If I do one of them is muted. Or... When I'm watching a movie I cannot hear the system sounds (such as someone messaging me on Pidgin). Another scenario is when I am listening to music in Bansee I cannot check out a video even if I pause the music first. You probably get it.

I am still new to linux so forgive me I am being silly now. Thinking it can be a Pulse Audio issue I checked out stuff in some of the guides in the forum first. As far as I can understand ALSA drivers go through Pulse Audio somehow. And a number of applications can easily run if I select the Standard Output driver for Audigy 2 ZS. Applications using that show up on Pulse Audio manager. However when the Multichannel Playback driver is selected for any application I cannot observe the output in Pulse Audio manager. It doesn't seem to go through Pulse Audio at all. And the standard playback is of no use to me. (sound comes only from 2 speakers... )

This problem does not exist on Kubuntu btw. Things work perfectly. Also in Kubuntu the when the standard playback driver is selected Kmix still allows me to play around with all the channels and I get surround sound... 

Now I have found a ghetto solution for this. For system sounds (Sound Events) I selected Pulse Audio Sound Server. This allow system sounds to play even if I have a movie running. For music playback I installed Amarok now, and probably because it doesn't use Gstreamer and uses Xine, Amarok is uneffected. Music playback can go on while a movie is playing. But this is not really a solution. I simply cannot put a movie on pause and listen to music or vice versa using GNOME applications. 

Any ideas?

---

