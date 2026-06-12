---
title: "Disabling a sound card"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by explosive on 2006-06-20
HI,

My Xubuntu install has 2 sound cards recognised. My onboard laptop sound card and my external USB Creative Sound Blaster. I would like to disable the onboard sound card so that the external card is always used.

Could anyone explain how I can accomplis this.

(BTW there is no option in the BIOS to disable the onboard soundcard).

Thanks :)

---

### Post by freakish on 2006-06-20
i would like to know this too...i want also to disable the onboard sound card

---

### Post by jonathantneal on 2006-06-20
I just was checking the forums for the exact same scenario.  I have two sound cards, a Creative LIVE and E-MU 1820; the 1820 is far (likely) from being Linux compatible.  However, the system continually tries to use the 1820 by default, so I need to disable it in Ubuntu.

---

### Post by zob on 2006-06-20
Please help these guys (and me). I have the exact same problem. I have an EMU-0404 sound card. Sadly without linux support (it is nice though). I need to disable it to make my onboard sound card work.

---

### Post by Krister Hallergard on 2006-06-21
My problem is similar, as apart from my onboard sound card the TV tuner card is also detected as sound card, more often than not as the first card and then I have no sound.  Would like to disable the TV tuner card

---

### Post by Krister Hallergard on 2006-06-22
You might want to try
     asoundconf set-default-card CARD
where CARD is the name of your card in e.g. KinfoCenter that you want to prioritize.  I did not get all audio programs to work with this, see my separate post!

---

### Post by Krister Hallergard on 2006-06-25
Believe I found a solution to disable my TV Tuner card: added the line "blacklist saa7134_alsa" to /etc/modprobe.d/blacklist

---

### Post by ekuliak on 2006-06-25
I disabled my onboard sound card by disabling it in BIOS.


EDIT: I noticed the original poster said BIOS didn't allow it to be disabled.  Weird.
I'm gonna leave my post as is in case it will help somebody :)

---

### Post by TomG24 on 2007-05-04
I'm sorry my late response to this outdated topic, but I ound this topic while searching for a a solution for a similar problem with a AC '97 onboard audio of my Asus A8V Deluxe motherboard.

As mentioned by someone, disabling the onboard soundcard in the bios could help, but unfortunately, this doesn't seems help on my system. The soundcard is still detected and used in Ubuntu (Windows doesn't seems to reconize it anymore).

The soundcard that I want to use in stead of the onboard one, is a Creative Sounblaster Live! 5.1. Altough the Creative card is detected correctly by Ubuntu, it seems to be it's not configured as the default soundcard.

So, what I actually did was checking what modules are loaded during startup with the command "modprobe -l"
After that, I searched fore a string "97" (modprobe -l | grep 97) to show up the loaded modules for the onboard soundcard.
And finally, I blacklisted those modules (the one's that are related to sound/audio) in /etc/modprobe.d/blacklist.

I came up with this list:

```

#Disable onboard AC '97 audio"
blacklist snd-ak4531-codec"
blacklist snd-ac97-codec"
blacklist ac97_codec"
blacklist ac97_bus"
blacklist snd-via82xx"
blacklist snd-via82xx-modem"
blacklist via82cxxx_audio"

```

Hopefully it could help for others too, probally having a similar hardware configuration.

[SIZE="1"]ps: Apologizes for my bad English, since it's not my native language[/SIZE]

---

### Post by ronocdh on 2007-05-04
This was very helpful to me, TomG24. I've bookmarked it for later use on a system on which the user broke off a plug in the speaker output jack! I had to install a new soundcard, but wasn't able to tell Ubuntu to ignore the onboard one. Thanks a lot.

---

