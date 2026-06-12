---
title: "Mic cuts out after random time with Skype"
date: 2009-04-20
forum: Multimedia Software
---

### Post by chadjohnson on 2009-04-20
Hi,

I am on Ubuntu Hardy (Mint 5, Elyssa, actually, which is a derivative of Ubuntu). Each and every time, without fail, that I try to do a conference call with my co-workers, the mic stops working with Skype. I can hear everyone else, but no one else can hear me. They CAN almost always hear me at the beginning of the call, however.

I first thought it was a conflict between Skype and Firefox (or Flash), but after closing Firefox and running ps aux to make sure it isn't running, the issue STILL manifests itself.

I previously followed the steps here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) (several months ago), and this solved a similar problem where Flash was dominating the sound output, subsequently disallowing other desktop apps (Skype included) to use the sound while Flash was running.

Has anyone else experienced this isssue, where their mic randomely stops working in Skype? Does anyone know how to fix the issue?

---

### Post by chadjohnson on 2009-04-20
bump

---

### Post by chadjohnson on 2009-04-21
So...this sucks. Can anyone help? All I need is a link to a howto or something.

---

### Post by DJonsson2008 on 2009-04-30
I'm having a similar problem. Every other form of sound works
fine on this Ubuntu/Xubuntu 8.4 machine. 

But when making test calls in Skype -- the sound breaks up,
like a mobile phone entering a tunnel -- that is the sound is intermittent.

Calling friends they say the sound is breaking up with some words
getting through and others not.  I've tried increasing the 
processor priority via the processes tap of system monitor for
Skype but that does not help. I can hear calls as clear as a graham bell, but outgoing voice seems to have a problem. 

Looking at processes in system monitor I do not see pulseaudio running,
I'm using an otherwise robust USB Creative sound card with generic USB audio driver/Ubuntu setup, with Microphone and Headphone going through the Alsa mixer, its clear the microphone is working, but Skype can't hold the signal somehow.

Any clues, conspiracy theories, ancient herbal cures or scientific insights appreciated?

---

### Post by JohnReid on 2009-08-02
bump

---

### Post by igorzwx on 2009-08-02
I solved my problems with Skype by installing OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

You have two options:

1. ALSA without PulseAudio
2. OSS4 (without alsa and pulse)

To install OSS4 on Ubuntu 8.04,
you should compile it (from Mercurial).
And you should blacklist some alsa modules manually.
See my howto here:
	  [Howto: OSS4 with Ubuntu Lite (Beta, netboot)]("http://www.4front-tech.com/forum/viewtopic.php?t=3237&sid=efc361bc85845cc28e5eb7a2e4758df8")
		[http://www.4front-tech.com/forum/viewtopic.php?t=3237&sid=efc361bc85845cc28e5eb7a2e4758df8](http://www.4front-tech.com/forum/viewtopic.php?t=3237&sid=efc361bc85845cc28e5eb7a2e4758df8)

---

### Post by chadjohnson on 2009-08-02
I finally got it working by installing Jaunty and doing some special configuration. Notes on this [here]("http://chaddjohnson.springnote.com/pages/3558911?read=1").

Note that I still have a problem when I play something with Flash Player 10 in Firefox and then try to use MPD--MPD won't work without restarting Firefox. Other than that, I have not had any problems with Skype. I did have to make sure to select the correct sound inputs and outputs in the Skype settings.

Everything that was originally installed with the Ubuntu install is still installed.

Note that my sound card is a Sound Blaster Audigy 4 SE 7.1 24-bit.

Also note that on my HP Intel-based laptop running Jaunty I did not have to do any special configuration at all. Everything works on it just about as well as it does on Windows with little or no problems.

---

