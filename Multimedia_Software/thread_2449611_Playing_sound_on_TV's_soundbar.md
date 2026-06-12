---
title: "Playing sound on TV's soundbar"
date: 2020-08-30
forum: Multimedia Software
---

### Post by trifail on 2020-08-30
Hi,

I try to play videos on my TV with my laptop through HDMI, which work with the sound redirected to the TV speakers.
Unfortunately, I'm unable to play the sound on my Soundbar.
It's a 2.1 Denon soundbar which is connected to the TV via HDMI (to show on the tv the settings I guess) and via optical cable.

I have no problem with the nintendo switch or the android tv of the tv box however.

I can't figure out how to set up ubuntu to work with the sound bar through the TV, even with pulse audio.
Any help would be appreciated :)


Have a nice day

---

### Post by CelticWarrior on 2020-08-30
Welcome.

How exactly do you have connected (and set) the Nintendo Switch and the Android TV?

---

### Post by trifail on 2020-08-30
Hi,

I did not do something particular, just plug the HDMI cables to the TV. One of the port if for CEC (the one for the android tv) but the port for the switch is the same as the laptop.

---

### Post by CelticWarrior on 2020-08-30
If so it should work the same. Make sure the sound output is set to HDMI in Ubuntu, of course. Everything else is totally foreign to the OS, CEC is managed by the TV and regarding audio it's just a passtrough. Meaning: If the computer sends audio via the HDMI port to the TV then sending the same audio to the soundbar is managed by the TV itself. The devices connected to the TV are unaware (and can't be other way) of the soundbar.

---

### Post by SeijiSensei on 2020-08-31
Early on in the days of HDMI, I found that I could not send the audio signal to my TV via HDMI unless I had installed the NVIDIA driver for my graphics adapter. I don't know how true that is any more.

If you still can't track down the problem, install pavucontrol and make sure the output is being routed correctly through the HDMI device.

---

### Post by CelticWarrior on 2020-09-01
> [COLOR=#000000]Early on in the days of HDMI, I found that I could not send the audio signal to my TV via HDMI unless I had installed the NVIDIA driver for my graphics adapter. I don't know how true that is any more.[/COLOR]


Mostly true for most Nvidia cards. Nouveau has no HDMI audio output support except for a few older cards.

---

