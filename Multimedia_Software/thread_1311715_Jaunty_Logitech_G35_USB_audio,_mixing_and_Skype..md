---
title: "Jaunty Logitech G35 USB audio, mixing and Skype."
date: 2009-11-02
forum: Multimedia Software
---

### Post by 1clue on 2009-11-02
Hi,

I've been trying to get Skype working, and in the process went out and grabbed a Logitech G35 headset.

Skype works, but only if absolutely no other app grabs the headset.

I had it before where I could listen to music through the on-board sound card, and system beeps and whatever else would mix in so it was all playing as appropriate.

I can't get that to work anymore.  I've been around Linux for a decade or better, and have used it as my sole workstation for nearly that.  I've never tried any sort of video or telecommunications though, so I am lost here.  I've never had a USB audio IO device, and it seems to me that this is the problem.

If I don't select the Logitech directly in the Sound Preferences, the sound goes to the on-board sound card.  I've tried pretty much every permutation.  I can't use PulseAudio, which is what was going on before.

Now, no matter what, only one app gets the card.  If I have music or a video going, the system beeps don't sound off, and Skype says there's an error on output.  I quit every app that would use the sound card, and I can hook up in Skype again, or the system beeps go off.

Anyone know what I can do here?  Can I disable the default sound card altogether somehow, and convince the OS to go look for the G35 and use that through the mixer?

Thanks.

---

### Post by 1clue on 2009-11-04
Ok, it's working.

I had no idea there were so many Sound control panels, let alone that they all had to be configured if your setup is anything but basic.

I went to the [sound documentation]("https://help.ubuntu.com/community/Sound") and actually read through it.

For all my fellow lazy users who don't want to read the docs:

It turns out that these headphones have a built-in sound card.  I'm guessing that my problems came from Linux getting confused about which one to use.  I now have both sound cards playing the same stuff, and the settings actually survive a reboot.

---

