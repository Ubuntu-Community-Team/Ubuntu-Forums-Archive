---
title: "How to get the same sound implementation in Intrepid that Hardy has?"
date: 2008-11-05
forum: Multimedia Software
---

### Post by RogueLegend on 2008-11-05
So I was pretty happy with my upgrade to Intrepid, no longer do I experience random log outs, loss of keyboard control, and a few other twitchy items that seemed to have no solution.

The issue I have is with trying to use headphones on my laptop. I am aware that there are a few posts *related* to this, I have read them, but the symptoms are not necessarily *exactly* the same.

Another way to look at it is I'm looking for a different solution than the ones presented, as they do not work to my full satisfaction.

Here are the symptoms after the upgrade from Hardy to Intrepid:

A) In order to listen via headphones I must enable "Headphone as Line Out" and "Analogue Loopback" switches.

B) After I perform these steps, with headphones plugged in, a light hissing/static noise comes from the front speakers on my laptop, and feedback results- to remedy this, I must mute all recording mixers.

C) The output sound seems unusually low and extra tinny on both headphones and front speakers compared to my previous Hardy and Windows installs (Hardy and Windows sounded exactly the same).

D) Setting the Master Playback Mixer to anything below 50% of maximum volume results in the sound being inaudible (essentially muted). In hardy, it seemed to have a linear progression of volume control, with mute being at the very bottom of the master mixer, while Intrepid seems to have exponential progression, muting at halfway down the mixer.

I have tried:

A)Enabling all Playback and Recording Mixers, as well as all Switches and options.

B) With all Mixers and switches/options enabled, I tried every seemingly logical combination of muting outputs/inputs in order to get it to behave like the sound implementation in Hardy (automatically switching to headphones/muting front speakers when they are plugged in, relative volume being the same, and non-tinny sound coming out of the speakers).

C) Downgrading from ALSA 1.0.17 to 1.0.16  (the version used in Hardy).

D) Using the troubleshooting steps listed at the top of this forums (compiling own drivers, etc.

E) A clean install. 

My configuration:

Dell Inspiron 1535 with 4 gb of RAM.

lspci -v shows:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
	Subsystem: Dell Device 0254
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f6ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel



My primary question is this: what components/packages/drivers do I need to remove/add to get the same sound implementation in Intrepid as  I had in Hardy? Is this possible?

I apologize if it *seems* like I am reposting the same problem, but as I mentioned, it doesn't seem as if others are experiencing the same set of symptoms as I am (although some symptoms are the same, not all are) and I am asking for a different solution than  what has been provided. Given those two facts, I believe it warrants a separate thread.

In addition, I don't want to leave Intrepid, as it solved pretty much every other issue I had. I greatly appreciate any assistance that anyone can provide.

---

