---
title: "Terrible sound quality"
date: 2012-05-17
forum: Multimedia Software
---

### Post by Woegjiub on 2012-05-17
I reinstalled yesterday (12.04), and have noticed that the audio quality is absolutely awful.
Music sounds as though it is clipping even at lower volumes; there is a great deal of static over the sound.

It worked fine before, and the only thing which has changed is the install.
It happens in amarok and vlc, which are the only two programs I have installed capable of audio playback.
I have attempted lowering the volume in kmix to about a quarter, and raising it on my speakers, but the distortion is still there. The EQ is disabled in amarok, and the volume is at 100% in VLC.

Could anyone help me?
Would it be worthwhile removing pulseaudio and using only ALSA?

---

### Post by Face-Ache on 2012-05-17
Just a suggestion; you could try going into the VLC settings, Audio, and then changing the Output mode from Default to either ALSA or PulseAudio. That's worked for me a couple of times when the music has sounded all scratchy and distorted.

Or even try Banshee - should have been installed by default.

---

### Post by carl4926 on 2012-05-17
Which backend is set in the kde settings

The options should be: gstreamer, vlc or xine

I use gstreamer (though that's in openSUSE)
make sure you have all the gstreamer codecs

---

### Post by Woegjiub on 2012-05-17
> **Face-Ache said:**
> Just a suggestion; you could try going into the VLC settings, Audio, and then changing the Output mode from Default to either ALSA or PulseAudio. That's worked for me a couple of times when the music has sounded all scratchy and distorted.

Or even try Banshee - should have been installed by default.
That works for VLC, but I am not keen on installing all of the gnome dependencies Banshee would pull in; I am running kubuntu.

---

### Post by Woegjiub on 2012-05-17
> **carl4926 said:**
> Which backend is set in the kde settings

The options should be: gstreamer, vlc or xine

I use gstreamer (though that's in openSUSE)
make sure you have all the gstreamer codecs
Gstreamer. I presume I do, as gstreamer is the only option in the settings dialogue, and the files are being parsed.

Disregard everything, it turns out the song was *meant* to sound like that. I feel really stupid now.

---

### Post by Face-Ache on 2012-05-17
> **Woegjiub said:**
> That works for VLC, but I am not keen on installing all of the gnome dependencies Banshee would pull in; I am running kubuntu.

Oh sweet! Pleased you got it sorted out.

Banshee was just a suggestion for if the VLC option wouldn't work - didn't realise you were running kubuntu.

---

