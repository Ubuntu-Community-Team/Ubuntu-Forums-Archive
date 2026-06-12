---
title: "Ubuntu &amp; Pulseaudio, we need a choice"
date: 2010-03-24
forum: Multimedia Software
---

### Post by dlmarti on 2010-03-24
For some reason Ubuntu wants pulseaudio, tbh I don't know why, but I accept that its a done deal.

But why not give the users the choice?  Many older games, and several key applications will NEVER work under pulseaudio.

An ALSA based Linux distribution just works, why mess with it?  How many people really need to distribute system sounds onto a different box?

9.10 removed the ability of the user to back away from pulseaudio, that was a huge mistake.  Subsequent releases of Ubuntu, need to preserve the ability of the user to back off of pulseaudio.

And yes I fully understand that Ubuntu screwed up the pulseaudio setup, but it wouldn't have mattered.  The design of pulseaudio is fundamentally flawed, and it will never work.

For example, Skype;  With pulseaudio Skype looses the ability to ring on your main speakers, while still using your headset for normal communications.

And thats the kicker, pulseaudio makes some key assumptions on how your going to use the audio resources.  This removes the ability to do some really cool stuff (like supporting multiple audio cards with the same application).  In return pulse audio gives you; 
1. crappy support for older machines (its a resource hog).
2. the ability to distribute audio to other boxes (honestly how often are you going to need this?).
3. the ability to mix based on application (wow, we already had this in ALSA, and it worked).

In closing, I'm not asking you not to include pulseaudio, just not to lock us into it.  The users don't want or need pulseaudio, so why force us into it??

---

### Post by wkulecz on 2010-03-24
I'm with you here, it seems just when ALSA started to be something that "just worked" they throw it out for something "better".  

Along the same line of reasoning, I suspect the Grub2 switch will be a real nightmare for the dual boot folks once 10.04 is released.

---

