---
title: "Ubunti Studio 9.10 - Tascam US-122 - no sound with Jack"
date: 2009-12-22
forum: Multimedia Software
---

### Post by wbm on 2009-12-22
Hello, I looked through threads here and on the web about this going back to 2005.
My problem seems to be a little different though.

I have a fresh install of Ubuntu Studio 9.10 and installed the 2 drivers for the US-122.
In Preferences < Sound the Tascam shows up as both an input and output device. I can record sound and I can hear sound. The green light is on.
But, as soon as I launch Jack, no more sound. I can see the leds working in a synth through Jack, but I can hear no sound.

Anybody have a suggestion please? Thanks!

---

### Post by Ubuntaqua on 2009-12-22
Did you remove pulseaudio or is Jack supposed to work with it ? In the second case, there's a jack module for pulseaudio to install.

---

### Post by wbm on 2009-12-22
> **Ubuntaqua said:**
> Did you remove pulseaudio or is Jack supposed to work with it ? In the second case, there's a jack module for pulseaudio to install.

Thank you for replying.
Could you please elaborate on this a little?
I did an install of Ubuntu Studio 9.10

Why would I remove pulseaudio (assuming it was installed with the Ubuntu Studio install)

What do you mean by: is Jack supposed to work with it?

If I install pulseaudio-module-jack (assuming that's the one you mean), what will that do to my existing non-jack applications and why would that make my Tascam work with Jack.
I did some research, and it seems all this has to do with what hardware gets grabbed by which module first.
Please keep in mind that without Jack everything already works (and I'd like to keep it working).
Only when Jack launches, I get no sound.

---

### Post by jvanloonofagej on 2010-01-22
Hey WBM, did you ever get this working?  I'm so frustrated with the fact that I can't get anything (either the us 122 or the USB microphone I have) working with Jack that I'm about to return to Windows.  The USB Mic at least worked in 9.04...

My suspicion is that this is all a conflict between jack and pulseaudio, as I can record sound from my usb mic from the command line in arecord, and I can see audio levels dancing when speaking into the mic in the pulseaudio volume control, but I get nothing in Jack.

I'd love to know if you got it to work...

---

### Post by wbm on 2010-01-22
> **jvanloonofagej said:**
> Hey WBM, did you ever get this working?  I'm so frustrated with the fact that I can't get anything (either the us 122 or the USB microphone I have) working with Jack that I'm about to return to Windows.  The USB Mic at least worked in 9.04...

My suspicion is that this is all a conflict between jack and pulseaudio, as I can record sound from my usb mic from the command line in arecord, and I can see audio levels dancing when speaking into the mic in the pulseaudio volume control, but I get nothing in Jack.

I'd love to know if you got it to work...

I actually did get it working. For me the mystery button was in the Jack setup. The audio input device had some weird name for the Tascam 122.
But, everything works.
I'll check my notes tonight and post back over the weekend.

---

### Post by cordetese on 2011-03-12
> **wbm said:**
> I actually did get it working. For me the mystery button was in the Jack setup. The audio input device had some weird name for the Tascam 122.
But, everything works.
I'll check my notes tonight and post back over the weekend.

I have the same problem... please! Can you be more explicit and describe how you get the soundcard works?

Thanks a lot!

---

### Post by RgnKjnVA on 2011-08-13
> **wbm said:**
> I actually did get it working. For me the mystery button was in the Jack setup. The audio input device had some weird name for the Tascam 122.
But, everything works.
I'll check my notes tonight and post back over the weekend.

+1 looking for that reply. I'm stumped as well by my US-122. Really frustrating part is that it worked previously but, mysteriously, I can't get any output now. Oh, the joys of OSS. I see the meters going but no audio. Jack doesn't seem to see my us-122 as an audio output when mucking with the Patchbay in qjackctl though it sees the midi outputs (?!)

---

