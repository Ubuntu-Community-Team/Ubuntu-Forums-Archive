---
title: "Configuring Skype audio"
date: 2010-12-18
forum: Multimedia Software
---

### Post by Peter Bell on 2010-12-18
Hi all!

I'm running Ubuntu Maverick on an Intel H55 mobo.  I have the sound configured to output through speakers on my monitor, via HDMI.  That has been working fine.

Last night I installed Skype (2.1.0.81) in order to chat to someone back in UK.

When I go to the sound devices configuration in Skype, each of the devices (Microphone, Speakers and Ringing) only have a single choice: 'PulseAudio server (local)'.

In order to get my usb-connected phone handset working with Skype I have had to go to the main sound preferences and alter both input and output to '9980 Analog'.  This works fine - I can make a Skype test call and playback my own voice.  However, all my system sounds now go out on the usb phone handset - also the Skype ring goes to the handset, which is pretty useless because it can't be heard from more than a couple of feet away.

How can I make Skype use the 9980 device for voice in and out, and use the system speakers 'Internal Audio Digital (HDMI)' for the ringing, while leaving all the system sounds to go out on the HDMI output too?

I'm sure that I managed to make Skype work much better on an older system (using Gutsy, or Intrepid???).

It seems, to me that there is a lack of fine audio control in my system - any assistance/guidance would be much appreciated.

---

### Post by xc3RnbFO8P on 2010-12-19
> However, all my system sounds now go out on the usb phone handset
In Sound Preferences> Sound Effects> Sound Theme, you can select None.
> also the Skype ring goes to the handset, which is pretty useless because it can't be heard from more than a couple of feet away.
Have you tried to change speaker to usb phone before you answer the call?

---

### Post by Peter Bell on 2010-12-19
Thank you for your reply!

> **Ringi said:**
> In Sound Preferences> Sound Effects> Sound Theme, you can select None.

Yes, of course that is possible, but rather defeats the object of having system sounds.

> Have you tried to change speaker to usb phone before you answer the call?

Again, possible, but rather clumsy.

Surely, it must be possible to configure system sounds (and Skype ring) to go to the speakers, and have the Skype voice call go to the usb handset, without having to fiddle around everytime one makes or receives a call.

This is how it used to work in a previous installation of Ubuntu/Skype.

---

### Post by xc3RnbFO8P on 2010-12-19
You can try PulseAudio Manager (in Synaptic Package Manager)
I haven't used it, maybe  someone can help you with that.

---

