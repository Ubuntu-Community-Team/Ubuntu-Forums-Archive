---
title: "No Sound in Oblivion (via Steam, via Wine)"
date: 2012-03-01
forum: Multimedia Software
---

### Post by CidNight on 2012-03-01
First off - I am very new to Linux.  Just thought I'd state that straight out.

Here's what:  I recently installed Wine in order to install Steam in order to install Oblivion.  I followed the guide @ [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux) and, with some hitches here and there, got everything working.  The biggest issue was figuring out that, having an ATI card, I had to change some registry settings in order for the entire world to not render as the color blue.  It may be worth noting that most guides assume that you are running Oblivion from disk, rather than through steam - so that could have an effect?

Unfortunately!  I now have the game up and running but it has absolutely no sound.  No music and no SFX.  

Before playing I ran the following tweaks to the registry:
bForce1XShaders=0 
bSaveOnInteriorExteriorSwitch=0
SIntroSequence=
bUseWaterShader=0
 bUseJoystick=0
 bMusicEnabled=0

[FONT=Verdana]And I tried changing to "bMusicEnabled=1", but that made no difference.[/FONT]  I have run
other tweaks in game including turning off grass, leaves, and LightBright
(or whatever) to improve frame rate, but those were after the sound
wasn't working.  Any ideas?

Oh, also, changing settings to sound in game seems to have no effect.

---

### Post by lite1979 on 2012-03-08
Have you tried wineconfig (Applications>Wine>Wine configuration

There should be an audio tab that lets you choose which driver wine uses. I use alsa right now, but I've had success with others as well. There should be an option to test for sound as well.

---

