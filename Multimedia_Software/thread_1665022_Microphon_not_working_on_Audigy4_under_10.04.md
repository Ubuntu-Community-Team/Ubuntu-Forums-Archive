---
title: "Microphon not working on Audigy4 under 10.04"
date: 2011-01-11
forum: Multimedia Software
---

### Post by _mOrgoth_ on 2011-01-11
Please help me here cause I'am desperate...
I am googling and surfing all over the net and this forum (and other forums) and can't find solution. Sound is working perfectly but microphone.. NOOOO!!
It is not broken cause it work under Win7. Till now:
Under sound preferences device is: SB0400 Audigy2value
                                   1output/1input
                                   Analog stereo duplex
                                   Under profile: analog stereo duplex
Tried all kinds of combination with alsamixer over console and gnome-alsamixer. 
Alsamixer console-Card SB Audigy 4 [SB0610]
                  chip:SigmaTel STAC9750,51
                  everithing that deals with mic is enabled
Gnome-alsamixer: Under soundcard properties everything is enabled. Card model is SigmaTel STAC9750,51
Also tried to reinstall Alsa..no help..
Installed pavucontrol..
Under configuration is: SB0400 Audigy2 Value
profile: analog stereo duplex
Under input device: SB0400 Audigy2 Value Analog Stereo
port: analog microphone/microphone 1
Front left 0%, Front right 63% show:all except monitors (on some forum find that this is the best setting)
When I start sound recorder and Audacity it records nothing. Please help cause I have no idea what to do..(read this as smashing my head against the wall):(:confused:
P.S. It worked fine under 9.10

---

### Post by unimatrix on 2011-01-11
I believe 10.04 had some problems with recording. I remember it didn't work for me either. Try upgrading to 10.10.
Also, consider buying a better sound card (for example, something that isn't made by Creative or Asus). Seriously. I've had the same card you have and it was nothing but trouble. It's so bad I can't even sell it because nobody wants to buy it.

---

### Post by _mOrgoth_ on 2011-01-11
> **unimatrix said:**
> I believe 10.04 had some problems with recording. I remember it didn't work for me either. Try upgrading to 10.10.
Also, consider buying a better sound card (for example, something that isn't made by Creative or Asus). Seriously. I've had the same card you have and it was nothing but trouble. It's so bad I can't even sell it because nobody wants to buy it.
Ok.. big thx for advice.. Ironic is that i bought this card cause mic didn't work on my onboard card... LOL!!!
So.. I will try 10.10 and than will see. Till than I am in temptation to try this:
[http://ptspts.blogspot.com/2009/09/how-to-get-rid-of-pulseaudio-on-debian.html](http://ptspts.blogspot.com/2009/09/how-to-get-rid-of-pulseaudio-on-debian.html)
read on some forum that pulseaudio is responsible for my problems. Anyone tried this? Some kind of other solution?

---

### Post by unimatrix on 2011-01-11
Don't do that. You will create much more problems than you will solve.

But you might consider going over to the #pulseaudio channel on the FreeNode IRC server. They're usually pretty helpful.

---

### Post by _mOrgoth_ on 2011-01-11
> **unimatrix said:**
> Don't do that. You will create much more problems than you will solve.

But you might consider going over to the #pulseaudio channel on the FreeNode IRC server. They're usually pretty helpful.
Thx!! You have Big virtual beer:)

---

### Post by unimatrix on 2011-01-11
Hvala. Hehe :D

---

### Post by MeduZa on 2011-01-28
I have the same sound card, I like it because the HMIX and the good quality, the problem is, pulseaudio is not necessary when you have that sound card ( the card made the mixing via hardware)
so After update to 10.04 = no mic, all works but no mic.
I fixed the problem removing pulseaudio and setting back ALSA, card works perfect but I lost volume control so I used a PPA with Gnome using alsa, and everything start working again.
Today I installed the 10,10 and the problem is back, so I thing I will remove pulse, also if I try to open the sound recorder program I get an error:
Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System Preferences menu.

but my settings are fine, is a pulseaudio bug / problem.

The card works perfectly on ALSA, no SOFTWARE mixing and MIC works.

---

### Post by MeduZa on 2011-01-28
UPDATE. ok I give pulseaudio a second chance. I start checking for stupid errors on my settings after the update, and I found one

the capture options on the alsamixer have 1 lever for every capture device, also with SPACE you turn it on or off, the MIC is turned on, but THE MASTER is OFF.

now the mic is working, 5,1, the pulseaudio works fine, but no HMIX :(

---

