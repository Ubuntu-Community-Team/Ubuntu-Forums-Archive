---
title: "Mute master does not mute all"
date: 2009-01-12
forum: Multimedia Software
---

### Post by NeonBible on 2009-01-12
My keyboard has built in volume buttons.  I can turn up and down the Master volume slider and can also mute.

But using Pulse in 6 channel mode, muting master only mutes the front 2 speakers.  How do I get Master to mute all? Also I noticed there is no Front speaker volume control.

I installed Pulse Volume Control and this allows me to mute everything when viewing the application.

I want either a keyboard shortcut to cut all sound, or a button in the taskbar to do it.

Can I achieve this?

---

### Post by NeonBible on 2009-01-12
Ok I figured I needed to go to System->Preferences->Sound and set the default mixer tracks and select the ones I wanted to control.

Now they are locked at the same level.  I want to create an offset as my LFE channel is normally slightly highter, as are the rear speakers.

Can I do this?

Why can't it just have one Master volume slider which controls all? :(

---

### Post by secondstage on 2009-01-12
I believe that this can be done by going to System > Preferences > Sound. Then under the "Default Mixer Tracks", choose the devices that you want to control with the Master Volume Slider. You would probably be most interested in the Options for Alsa Mixer, and OSS Mixer.

By the way, have you checked your [post]("http://ubuntuforums.org/showthread.php?t=1027172") about surround sound? Just thought that you might want to know that.

---

### Post by NeonBible on 2009-01-14
> **secondstage said:**
> I believe that this can be done by going to System > Preferences > Sound. Then under the "Default Mixer Tracks", choose the devices that you want to control with the Master Volume Slider. You would probably be most interested in the Options for Alsa Mixer, and OSS Mixer.

By the way, have you checked your [post]("http://ubuntuforums.org/showthread.php?t=1027172") about surround sound? Just thought that you might want to know that.

Thats not quite it.  As I said I have done this,  I can mute all with a single button. But when I change the volume or mute, they all reset to the same level.  I want them to be offset and change volume so that they are relative to each other.

---

