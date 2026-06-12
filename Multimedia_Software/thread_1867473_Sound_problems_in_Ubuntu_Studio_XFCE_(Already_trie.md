---
title: "Sound problems in Ubuntu Studio XFCE (Already tried the guide)"
date: 2011-10-23
forum: Multimedia Software
---

### Post by Black_Sector on 2011-10-23
OK, so sound WAS working ok. Im not sure what broke it. Sound card shows up, video card shows up, drivers installed. Trouble shooting yielded no results. I did not find an "ALSA driver" for my video card when I followed that link, it looked more like a 'how to', but I have the right driver for my video card and I know video cards can interfere with sound.

I can only get sound out of my front mic, but it sounds terrible and full of fuzz. I cant get sound out of the rear line/mic out, or out of my sound card directly OR out of my USB headset.

I installed the Backbox XFCE desktop on an Ubuntu Studio base, and added other multimedia software.


I never thought I would say this, but I think I would like to isntall Pulse Audio controls instead of the ALSA mixer. I know it breaks a lot, but the design is nicer and its easier to choose your input and output devices, where in the ALSA mixer its not exactly clear whats going on.


How do I get a different sound mixer in XFCE?


Any suggestions for further trouble shooting?

---

### Post by Black_Sector on 2011-10-23
I temporarily fixed my problems by installing Gnome with Gnome Classic, changing my settings in Pulse Audio, then when I came back and used the ALSA mixer in XFCE/Backbox the sound was working again.

---

### Post by veromarybr on 2011-10-23
Did you install Gnome just to get pulseaudio?

I'm wrestling with mythbuntu 11.10 which uses xfce.  At first there was no sound, but all the drivers seemed to be there and there were no errors - just no sound.  pavucontrol  has a nifty bar which shows how much sound its putting out - rising and falling like on the front of a fancy stereo.  But no sound from internal speakers or headphones.  Changing settings with pavucontrol to set the output device to Digital Out gave really BAD sound through the headphones.  Tried rebooting with the liveCD and sound works there alright.  Reboot the computer and now no sound - until I plug the headphones in then the noisy sound comes out the Internal Speakers. :confused:

I'll try installing Gnome but I don't understand how that would help.

---

