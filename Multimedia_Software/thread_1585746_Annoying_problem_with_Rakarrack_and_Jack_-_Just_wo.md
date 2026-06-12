---
title: "Annoying problem with Rakarrack and Jack - Just wont work"
date: 2010-09-30
forum: Multimedia Software
---

### Post by WalmartSniperLX on 2010-09-30
I have everything installed and Jack working fine. I'm in the user group and have realtime enabled and running. My problem is that I can't get my input (the guitar) through rakarrack and out. This is how it is set up:

Guitar is plugged in directly through the Input jack on the sound card (I have tried with the front input, rear, front mic, and rear mic inputs)

I have kde mixer set to allow pass-through of the sound from the input source (I can hear the guitar in my speakers, un-amplified directly from the source). 

The problem is that I cant get this source into rakarrack with jack to save my life. I have tried all sorts of combinations both physically with the audio jacks and in jack audio. Is that Jack isn't detecting the right input source with alsa or something?

---

### Post by WalmartSniperLX on 2010-10-01
In other words all I'm getting from Rakarrack is static, the output meter jumps up and down, and I can hear sounds from the effects but just no guitar from the input running through the program.

---

### Post by transmogrifox on 2010-10-01
This seems like you don't have your capture source configured & w/ volume up on the sound card.  Use alsamixer and tab to the capture sources.  Arrow over to your mic or line in (whichever you're using) and spacebar to mark it as a capture source.  Make sure the level is up on it.

Another thing you can do is start some music in totem and connect the outputs to the system outputs to see if the problem is getting sound out or getting sound in.  If you connect totem to the system outputs and can hear the music, then surely it is a capture source volume configuration problem.
Hopefully that helps :)

---

### Post by WalmartSniperLX on 2010-10-01
If there were a way for me to show you a lot of gratitude beyond just a "thank you", I would do so. But, Thank you! That was it! :)

---

