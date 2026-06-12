---
title: "Very bad recording quality after 11.10 upgrade"
date: 2012-02-04
forum: Multimedia Software
---

### Post by Muadib25 on 2012-02-04
Hello!

I recently upgraded to 11.10 and I noticed a very bad sound quality when I am trying to record with my microphone or talk through VoIP (voice too bassy and boomy).

I firstly suspected Pulseaudio, which I removed for working only with ALSA, as I did before the upgrade. Since this didnt solve anything, I also tried the mike to another PC and the same mike and computer with a Winz partition I have installed. 

The differences are like day and night. So I am thinking of reverting to an earlier ALSA driver.

Question: Does anyone know how I can do this through Synaptic or the command line?  :confused:


Thanks in advance!

---

### Post by Scott Baker on 2012-02-06
Howdy. I have a couple of questions for you. First, when you say recording, what do you mean by this? Are you attempting to record your own voice, or some other sounds (sound effects, ring tones, music, etc)? Next, which VOIP set-up are you using? I've noticed with SKYPE, that it sometimes barfs after an upgrade, and it's better to just uninstall it, then re-install it. With Ekiga, it's a matter of fiddling with some of it's settings after the upgrade. Any other info you can provide will be greatly appreciated.  :-k

---

### Post by adiasd on 2012-02-07
Hi Folks,

I have a similar a problem after installing ubuntu 11.10 (it is a fresh install, not an upgrade):

When I use skype everybody complains that is hard to hear me because my voice's sound is too low. I tried to increase the volume in the sound control up to the maximum and it didn't help too much because it increases the noise and didn't get that louder anyway. I tried also to use alsamixer and set the mic boost to the maximum but it didn't help (not sure if I'm using alsa or pulse anyway).

My soundcard is a Realtek ALC269.

Does anybody have a clue on that?

Thanks

---

### Post by Muadib25 on 2012-02-07
Hello again!

> **Scott Baker said:**
> Howdy. I have a couple of questions for you. First, when you say recording, what do you mean by this? Are you attempting to record your own voice, or some other sounds (sound effects, ring tones, music, etc)? Next, which VOIP set-up are you using? I've noticed with SKYPE, that it sometimes barfs after an upgrade, and it's better to just uninstall it, then re-install it. With Ekiga, it's a matter of fiddling with some of it's settings after the upgrade. Any other info you can provide will be greatly appreciated.  :-k

When I say recording I am talking about anything that has to do with the microphone, from recording to Audacity to talking to Skype and Teamspeak. What everyone hears (and from what I am able to record) is a bassy voice that has nothing to do with before. I have also tested the mike on the same computer, but on WinzXP, and using Skype Call Testing Service I could hear my voice as it should sound, so the mike works properly.

The soundcard is an onboard called C-MEdia Electronics CMI9761A+.
The ALSA version is 1.0.24+dfsg-0ubuntu2

So I was wondering if this whole thing would fix if I tried to downgrade ALSA... What do you think?

---

