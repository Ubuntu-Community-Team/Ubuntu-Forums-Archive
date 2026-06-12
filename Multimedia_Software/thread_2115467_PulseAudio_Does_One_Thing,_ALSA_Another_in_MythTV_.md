---
title: "PulseAudio Does One Thing, ALSA Another in MythTV or MythBuntu"
date: 2013-02-13
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2013-02-13
Please bear with me while I try to even describe this problem. Words fail me.

This is a 12.04 box. I have installed MythTV (and now with some other updates, I guess I'm MythBuntu as well).

I use both the keyboard and a tv remote for changing volume. The keyboard has vol up, vol down and mute. All work as expected.

The tv remote is another matter. Once I press the Mute, I have to leave Myth and return to the desktop, open Audio Mixer, pull down to PulseAudio Mixer, un-check the Mute box and then the volume control on the remote will work again. 

I found this article: 

[Mute key mutes Alsa and PulseAudio, but unmutes only Alsa]("http://askubuntu.com/questions/118675/mute-key-mutes-alsa-and-pulseaudio-but-unmutes-only-alsa")

and tried the solutions there, but none have worked for me. And now, after trying them, the volume has started increasing on it own (to 100%).

Using Aptitude, I removed PulseAudio. Next, calling MythTV, the volume and mute controls on the tv-remote control do not allow for muting the sound. And when the sound is un-muted without PulseAudio being installed, the volume goes to 100% on it's own. I have re-installed PulseAudio.

If anyone could help me with understanding the guy's script, which I have place in /home/mark/.mythtv and have named the file: volumetoggle.

I could get the KB settings to accept this script, but when I touch the tv remote control MUTE button, and the Settings/Settings Manager/Keyboard/Application Shortcuts creates the shortcut, but, it still won't unmute.

I apologize if this is unclear. I have used MythTV about 10 days. I haven't worked with PulseAudio or ALSA in over 5 years.

---

