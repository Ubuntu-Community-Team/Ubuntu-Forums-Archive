---
title: "Strange problem with headphones..."
date: 2011-10-01
forum: Multimedia Software
---

### Post by ubersoft on 2011-10-01
I'm not sure whether this should be put here, or in the laptops forum, but I think I've managed to diagnose this as specifically a hardware issue, so I'm going to try putting it here.

I recently bought an ASUS G74S laptop. All in all it works spectacularly, but there are still three issues I'd like to get resolved. One of those issues has to do with how the sound card interacts with headphones, which is the topic of this post.

Summary: When I'm actively playing music and I plug in my headphones, the laptop speakers cut out like they're supposed to. However, no sound comes out of the headphone earpieces at all.

In the process of trying to figure out what the heck was going on, I fired up alsamixer. 

The attachment **alsamixer-no-headphone.png** (first thumbnail) is what the mixer looks like when there is no headphone attached. In this example I'm playing music at a fairly low volume level but it's still coming out of the laptop speakers pretty clearly.

Then I plugged in my headphones. Immediately the sound cut off. The attachment **alsamixer-yes-headphone.png** (second thumbnail) is what the miser looks like with the headphone attached. You'll notice the Speaker channel is set to 0<>0.

When I increased the volume on the Speaker channel in alsamixer, sound started coming through my headphones. Which is good! That's what I want! The sound came through the headphones and not the speakers -- so obviously alsa and the laptop are mostly working correctly, in that when I plug in a pair of headphones into the headphone jack, the sound goes to the headphones instead of the speakers. However, for some reason, each time I do this, the headphone volume cuts off.

Now... this wouldn't be a hassle, if it weren't for kmixer and pulseaudio. When PulseAudio is running, kMixer doesn't like to display all the channels alsamixer does. In fact, on the Payback Devices tab you only see two channels, as shown in the attachment **kmix.png** (third thumbnail). And the "Internal Audio Analog Stereo" channel correlates to the Master channel in alsamixer.

So my question is... is there a way to keep the speaker channel volume constant when switching over from the laptop speakers to the headphones? If not, is there any way to add the Speaker channel to kmix so I can control it manually?

Thanks for any help you can provide.

---

