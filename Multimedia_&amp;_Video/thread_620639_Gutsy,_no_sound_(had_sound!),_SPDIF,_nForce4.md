---
title: "Gutsy, no sound (had sound!), SPDIF, nForce4"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by stokkes on 2007-11-22
I think i've developed an ulcer and gray hairs in the past two days.. Never in my life have I tinkered so much to get something that should be so simple working. I just don't understand, nay, I can't fathom why things would be so difficult. 

I'm running Gutsy 7.10 on an AMD64 (in 32bit mode though) that has an onboard sound :

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Sound worked fine since I installed Gutsy, but then the fun really started happening. I wanted to get SPDIF working so I searched and rummaged through the threads here on the forums to attempt to find some way of getting SPDIF to work. Sound was being outputted from the SPDIF jack, however, it was PCM only (never 5.1). So i meddled and obviously, I did something I shouldn't have and now I don't have any sound whatsoever :(

Running alsamixer, I see that all my sound channels are NOT muted, volume is cranked as loud as it can go. Also, in the System -> Preferences -> Sound, everything is set to "Autodetect" (this is how it was before I started messing). I've also tried setting it to a specific sound hardware (CK804 is in the list), but I still don't get any sound.

I'm at my wits end, I Just want to throw this thing out the window .. I went from a system that had sound but no optical 5.1 working to a system that has no sound whatsoever working.

Desperately looking for some help with this.

**EDIT:** I should note that I can still use sound through the analogue out on my motherboard, but not SPDIF

---

### Post by skela on 2007-12-29
someone please solve this. i have the exact same problem! im so frustrated right now i havent a clue where to turn or what to do. no matter what i try i get no results...

anything out of the spdif doesnt work.
analogue sound from the normal jack does though.

i had the optical sound working, but was stupid enough to mess around with it to try to get the surround working...

---

### Post by skela on 2007-12-29
this may sound a bit strange, but i got results by reducing the volume of
IEC958 Playback AC97-SPSA
to 0 (yes all the way to the bottom) in the gnome sound control panel.

still cant get surround working though..

---

### Post by exactopposite on 2008-01-06
on my nforce4 system i had to change the device to nvidia ck804 AND  on the mixer window cick edit/preferences and select iec958. then iec958 will show up on the switches  tab. When the box is checked u should have sound from yout spidif output. at least it works that way for me.

it seems to only be stereo instead of surround though.

---

### Post by arman.haghi on 2008-02-09
One *Possible* Solution:

I have the same hardware (Abit Mobo with CK804 / AC'97 audio) and had the same problem; After ensuring Kubuntu was [_[COLOR="Blue"]recognising my hardware[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=205449") etc I kept searching for 'software' answers, but it turned out to be a hardware issue all along.

I was modding my box and had removed the front panel audio connections from my mobo. Having no connectors, I've learnt, disables the back panel audio unless you use jumpers across 5/6 and 9/10. Also, ensure that onboard sound is enabled (or auto) in your BIOS menu.

i.e.

If pins are

[FONT="Courier New"]: : : ' :[/FONT]

aka

[FONT="Courier New"]2  4  6  8  10
1  3  5     9 [/FONT]

then jumpers should be placed across 5/6 and 9/10

so

[FONT="Courier New"]: : | ' |[/FONT]

aka

[FONT="Courier New"]2  4  |  8  |
1  3  |     |[/FONT]


Hope this helps,

Arman.

NOTE: Check your motherboard manual first, hardware may vary.

My manual (ala example above) was at
[http://file.abit.com.tw/pub/download/manual/english/kn8-sli.zip]("http://file.abit.com.tw/pub/download/manual/english/kn8-sli.zip")

Solution Source
[http://forums.fedoraforum.org/showthread.php?t=171686]("http://forums.fedoraforum.org/showthread.php?t=171686")

---

