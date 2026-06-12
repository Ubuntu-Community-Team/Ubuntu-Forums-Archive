---
title: "Help, my audio just died!"
date: 2008-12-02
forum: Multimedia Software
---

### Post by kungmidas on 2008-12-02
This is a weird one...

Yesterday, I was using my PC as any other day. Just watching movies and surfing the web, no playing around with the system or installing anything. As far as I can remember, I didn't download any updates, but I might have forgot. Audio worked fine and have been doing so since long before 8.10, but I'm not sure if I used ALSA or PulseAudio.

When I turned of the computer, it stopped for a good while at "Stopping ALSA..." (I have the boot logo and text enabled). After a while, the screen would go black. I could type stuff and it would appear on the screen, but the only thing I could actually do was to press CTRL+ALT+DEL or the power button, which would just restart the shutdown from the top, and again it would hang at "Stopping ALSA...". I had to hold the power button for a couple of seconds to kill the computer.

When booting it again, sound was dead. All volume controls defaulted to "muted" on boot, but responded. There was no error messages displayed, but there were absolutely no sound in my speakers are all silent, no matter how much I raised every volume control I could find. I tried Amarok, Flash, VLC, Totem, and the System->Preferences->Sound... No sound.

I tried to reboot, every shutdown would hang at "Stopping ALSA...", and the sound would still be gone when I start the PC.



I had to give up, and tonight when I got back from work, I can reboot and shutdown just fine. However, sound is still dead.


And yep, audio works just fine in my Windows installation on the same PC...


Might mention, that just before turning off my computer (and when the sound died), my internet connection died (the cable company did some maintenance work). It's far fetched but I can't see ANY cause for how the sound could just break like that... =(


Any suggestions? Please?? =)

EDIT:
There is a pulseaudio process running. I've changed "autodetect" in Amarok to "pulseaudio", and made sure every volume control I could find are fairly high. Still no sound... =( pulseaudio process takes 5%-10% cpu when music is played, I don't know if that is more or less than usual.



EDIT #2:
Fixed. PCM had become muted. Going to file a bug report about this...

---

