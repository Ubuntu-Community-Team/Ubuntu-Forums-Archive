---
title: "i've just about had it with updates breaking my sound"
date: 2009-02-02
forum: Multimedia Software
---

### Post by sonicb00m on 2009-02-02
I seem to get into trouble with the sound card every time some kernel update comes out. The sound doesn't start up after reboot and i get this message in the sound panel

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I have the HDA Intel ALC662 installed and I've been blighted by sounds problems every few weeks or so using 8.10.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Nothing in this guide has helped me restore the sound. I am at the end of my tether. I am even considering dumping Ubuntu because of it.

I've been an avid user of Ubuntu for 3 years now but this is getting too much. This should not be happening all the time.

---

### Post by jrusso2 on 2009-02-02
Maybe don't do the kernel updates?

---

### Post by Neural oD on 2009-02-02
agree with jrusso2  - if something ain't broke - don't fix it - unless u want to do some tinkering :)

---

### Post by jocheem67 on 2009-02-02
I know what you mean, it's a frustrating thing.

My way to avoid problems is this:

In preferences --- sound I select alsa as backend ( no auto-detection or pulse )
The I use "asoundconf -list" to check on my available soundcards/chips ( I've got a multiple set-up )..this is just a command in the CLI.
With "asoundconf set-default-card" I can point alsa to the right soundcard...

Then it's just a matter of unmuting the card through the applet right above the screen...

I think pulse is often the "bad guy " here, just not stable enough...

---

### Post by sonicb00m on 2009-02-02
God dammit, I had uninstalled Pulse complete but somehow it's managed to sneak its way back into the system. It's not installed and doesn't appear in the sound manager but when i did apt-get remove pulse* a ton of libraries were removed and on next reboot the sound was back to normal.

Pulse audio is a bloody disaster!

---

