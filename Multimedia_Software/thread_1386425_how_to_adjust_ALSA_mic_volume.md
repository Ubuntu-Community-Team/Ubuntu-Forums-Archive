---
title: "how to adjust ALSA mic volume?"
date: 2010-01-20
forum: Multimedia Software
---

### Post by higashi on 2010-01-20
I'm using ALSA, and Alsamixergui. Everything's working fine, but my mic volume is really low. When i try recording something, i can barely hear anything. 

I tried adjusting the volume of "mic" in Alsamixergui, but that just makes me be able to hear my microphone through my speakers, and that's not what i want.

Thanks in advance.

---

### Post by sports.car.guy on 2010-01-20
You need to put the mute on your mic if the option is there. That way it is not directly fed to the speakers. It will still be recorded, always has been for me on cards with the capabilities.

If it does not have a mute don't worry, some don't. Then you will need to set it as capture. The ones without mute it usually stops a direct feed to the speakers when enabling capture. My X-Fi for example has no mute but has capture to check off.

If you don't have a check box for capture you need to select it in the actual capture "channel" for the mixer.

Like with Kmix you want to got to Settings>Configure Channels, then choose capture. It has a drop down, select mic on it and crank the volume on the mic and you should be all set. There may also be an option to expose a mic boost in your mixer.

If you do all that and the levels are still low you can build an Alsa mapping to boost the mic levels pretty easily and then send it to the capture.

I hope this helps.

---

### Post by higashi on 2010-01-20
i have mic on mute so that i dont hear it through my speakers. my mic still works with programs on my computer though... but it's still not loud enough. When i try to change the volume of 'capture', nothing happens. it just... ignores me.

---

### Post by LuridCinema on 2010-01-20
what program are you using ?

Im using audacity to record and it has record level adjustment function... tried that ??

---

### Post by higashi on 2010-01-20
well the programs i want to use it for the most is amsn and skype. But every program ive tried it on is the same low volume

---

### Post by AlexZaim on 2010-01-21
System> Preferenes> Sound> Input. There you have a mic amplifier

---

### Post by higashi on 2010-01-23
When i do that, i get a popup saying "waiting for sound system to respond". And it just stays there and waits forever.

---

### Post by ratcheer on 2010-01-23
Try alsamixer. It is a crude interface, but it gives you access to all the controls.

Tim

---

### Post by teresaejunior on 2010-01-23
Open a terminal and type alsamixer, like ratcheer said. Type <Right> until you find 'Mic Boost'. Then <Up> to increase the volume. Type <Esc> to save and exit.

If you don't find 'Mic Boost' you should maybe try a different sound setup in /etc/modprobe.d as root. There you can adjust your sound driver to your machine model.

---

### Post by higashi on 2010-01-24
when i do that, mic boost doesn't have a volume bar, and where it says "item" , it says "Mic Boost (+20dB) [Off] "

how do i turn it on?

---

### Post by teresaejunior on 2010-01-24
> **higashi said:**
> when i do that, mic boost doesn't have a volume bar, and where it says "item" , it says "Mic Boost (+20dB) [Off] "

how do i turn it on?

it is muted, press m on it

---

### Post by higashi on 2010-01-24
ok, it doesn't say 'off' anymore, but there's still no volume bar over it and i still can't adjust it ):

thanks for the help so far..

---

### Post by teresaejunior on 2010-01-24
But now you've got +20dB in your mic, which helps a lot, as you have mentioned before. In some boards you can't adjust the boost level, but you can turn it on or off. +20dB or off.

---

### Post by higashi on 2010-01-24
oh ok, thanks. :)

But now,whenever i try to record something, it only records into the left channel.. :\

---

### Post by teresaejunior on 2010-01-24
What app are you using to record??? try the alsa defaut recorder in the terminal, which will create a wave file: arecord

Then play it with aplay

---

### Post by higashi on 2010-01-24
that didn't make a difference, every app i use is only hearing the left channel .____.

---

