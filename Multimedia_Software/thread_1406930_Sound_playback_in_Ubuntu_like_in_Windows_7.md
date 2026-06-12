---
title: "Sound playback in Ubuntu like in Windows 7"
date: 2010-02-14
forum: Multimedia Software
---

### Post by d1brian on 2010-02-14
Is there any way to make Ubuntu play sound like Windows 7? I mean when i, for example, listen to music in Windows 7 the sound is much clearer and besides that i can use room correction to obtain a better surround feeling, but when i listen to music in Ubuntu the sound is not very clear and it sounds like stereo even though the sound is played back through all the speakers (the bass is also a little bit to high). 

So far i've tried installing the alsa driver and modifying the output levels of each channel, but didn't quite have the same result as the room correction feature in Windows, and the sound wasn't any clearer either.

Note: I have an onboard Realtek soundcard and Logitech x530 speakers

---

### Post by hxcobd on 2010-02-14
I'd recommend installing all of the Pulseaudio configuration packages from the repo:

- paprefs
- pavucontrol
- paman
- pavumeter

And tweak them to see if you can correct the problems.

You might also want to look into a media player with EQ or an EQ plugin.

---

### Post by d1brian on 2010-02-15
I installed those packages and i don't get very much control over the subwoofer. Regarding the fade between front and rear speakers: even if i put the front speakers at 50% and the rear ones at 100% i don't achieve the desired effect, and unfortunately it creates another problem: the subwoofer gets too loud. The playback sound exactly the same whether the profile is set on Analog Stereo Output or Analog Surround 5.1 Output :(

I am using audacious2 as my music player and i tried to move all low frequencies of the eq all the way down, and i noticed that the subwoofer doesn't cut out as it should.

---

### Post by VertexPusher on 2010-02-15
> **d1brian said:**
> The playback sound exactly the same whether the profile is set on Analog Stereo Output or Analog Surround 5.1 Output :(
Audiophiles would consider this a good thing. If a file is stereo, playback should sound like stereo. Everything else means that the sound gets mangled in some way. It may be what you have been used to, but it's not what accurate sound reproduction is about.

> I am using audacious2 as my music player and i tried to move all low frequencies of the eq all the way down, and i noticed that the subwoofer doesn't cut out as it should.
Realtek 5.1 sound cards have separate volume controls for all 6 speakers. You can reduce the subwoofer volume level.

---

### Post by d1brian on 2010-02-15
> **VertexPusher said:**
> Audiophiles would consider this a good thing. If a file is stereo, playback should sound like stereo. Everything else means that the sound gets mangled in some way. It may be what you have been used to, but it's not what accurate sound reproduction is about.

I know that's not what accurate sound reproduction is about, but the way Windows 7 does the upmix doesn't really sound like an upmix (at least from my point of view), and i was thinking that there could be a way to achieve similar results in Ubuntu.

> **VertexPusher said:**
> Realtek 5.1 sound cards have separate volume controls for all 6 speakers. You can reduce the subwoofer volume level.

I noticed that in sound preferences i could lower the subwoofer level but after a certain level i'd start to get a high pitch tone in the speakers (and becomes unbearable at minimum).

---

### Post by Eril on 2010-02-15
Hi d1brian, I have an onboard Realtek soundcard as well as 5.1 speakers and the sound also sounds less clear than in Windows 7. I have a quick question as well, if you go to the hardware tab in sound preferences and choose Analog Stereo Output, do you actually have stereo sound (as in sound coming from the 2 front speakers) or is sound still coming from all of your speakers? I'd assume that it should be stereo sound, but sound still comes from my rear and center speakers as well. I also really wonder why the sound is less clear too.

---

### Post by d1brian on 2010-02-15
> **Eril said:**
> Hi d1brian, I have an onboard Realtek soundcard as well as 5.1 speakers and the sound also sounds less clear than in Windows 7. I have a quick question as well, if you go to the hardware tab in sound preferences and choose Analog Stereo Output, do you actually have stereo sound (as in sound coming from the 2 front speakers) or is sound still coming from all of your speakers? I'd assume that it should be stereo sound, but sound still comes from my rear and center speakers as well. I really wonder why the sound is less clear though.

Honestly i didn't check the rear speakers or the center one, but one thing is for sure: when i switch to analog stereo output it's not quite stereo because i can still hear the subwoofer.

I'll check the rest of the speakers to see if it's more than a 2.1 output

---

### Post by d1brian on 2010-02-15
I tested to see whether or not there's any difference between Analog Stereo Output and Analog Surround 5.1 Output and as it turns out there isn't any difference in the way the sound is played back, i mean all the speakers play the same thing.

Could this be from the way Ubuntu handles the audio streams or could it be from the drivers?

---

### Post by Eril on 2010-02-15
> **d1brian said:**
> I tested to see whether or not there's any difference between Analog Stereo Output and Analog Surround 5.1 Output and as it turns out there isn't any difference in the way the sound is played back, i mean all the speakers play the same thing.

Could this be from the way Ubuntu handles the audio streams or could it be from the drivers?

Exactly. It's the same here really, If I select Analog Stereo Output sound comes from all of the speakers, if I select Analog Surround 5.1 Output it's basically the same playback as stereo. I'm trying to install the Realtek drivers found at their website, but I have no idea how to. If anyone could link me to a guide or how to I'd be grateful as I have no idea how to do so when I read the included readme (I'm rather new to Linux).

On another note, I've just noticed that if I select any of the Analog 4.1 Outputs no sound comes from the center speaker. This is fine. If I select Analog 4.0 Output however, it's the same as with the Analog 5.1 and stereo outputs. It's pretty strange, but I think it has to do with the drivers.

---

### Post by Yellow Pasque on 2010-02-15
> I'm trying to install the Realtek drivers found at their website, but I have no idea how to.
You don't need them. AFAICT, they just copied the ALSA source anyway.

> when i switch to analog stereo output it's not quite stereo because i can still hear the subwoofer.
That doesn't mean it's not stereo/more than 2 channels.

BTW, I had those Logitech X-530's too. I disliked them (too bassy, crappy mids) and gave them to a family member.

---

### Post by Deihmos on 2010-05-19
I have been messing with Ubuntu for a bit and that's one thing I realize. The audio quality sucks really bad when I compare to Windows 7. When i switch to 5.1 I get a lot of static when changing volume and the audio does not sound right.

---

