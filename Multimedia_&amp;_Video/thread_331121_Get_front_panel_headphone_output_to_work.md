---
title: "Get front panel headphone output to work?"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by gdinsdale on 2007-01-04
I have Dapper installed on an Athlon 3000, 1Gb RAM, Asus A8V-XE, Geforce 6600 system. I am having a problem getting sound to output through the front panel headphone connector on my case.

The sound is working absolutely perfectly through a 2.1 speaker system connected to the onboard sound connectors at the case rear. The front panel headphone/mic connectors are correctly connected to the correct place on the motherboard (they only connect 1 way).

When I plug headphones into the front panel socket music (or whatever) continues to play from the speakers and no sound is heard through the 'phones.

Does anyone have any ideas how to solve this?

Thanks :confused:

---

### Post by tenn on 2007-01-04
Might be a stupid question but is there a sound card and on board sound.
If there is only on board sound have you tried unplugging the speakers and than connecting the headphones.

---

### Post by Dekunuts on 2007-01-04
my guess would be that the front connections are muted, run alsamixer and check that. 

M mutes/unmutes

Up/Down changes volume

left/right scrolls

tab goes to capture devices

and escape exits the program

maybe this helps

---

### Post by gdinsdale on 2007-01-04
@tenn: Thanks for your reply. :) There is no separate sound card in the system, only the on-board sound. I'm at work at the moment but i'll try unplugging the speakers to see if that works when I get home.

@Dekunuts: Thanks for your reply. :) I read elsewhere about alsamixer but when I tried to run it I just got the "no such command"-type error. Do I need to add a particular package to get this? Like I said previously, sound works fine. I just can't get my headphones to work from the front panel.

---

### Post by Dekunuts on 2007-01-04
i think alsamixer comes with the alsa-utils package

---

### Post by eggdeng on 2007-01-04
Run ```
cat /proc/asound/modules
```

If you see snd_hda_intel, take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by gdinsdale on 2007-01-05
Ok tried the various things mentioned above. I've also been through the comprehensive sound guide thing on here. No joy on all fronts ](*,) 

When I do:

```
cat /proc/asound/modules
```

I do get snd-hda-intel (Thanks eggdeng ;) ) However, the post you linked to didn't help. I tried adding the line

```
options snd-hda-intel model=asus
```

to etc/modprobe.d/alsa-base but this just killed sound output completely.

In alsamixer I don't see the headphones port as a separate item if that's any help...

Any further ideas? :-k 

Thanks guys.

---

### Post by eggdeng on 2007-01-05
Check that your alsa version is at least 1.0.10rc3
```
cat /proc/asound/version
```. Try ```
options snd-hda-intel model=asus-laptop
``` or google around for similar options.

---

### Post by falstius on 2007-07-18
I had a similar problem until a few minutes ago and wanted to post a solution since I spent a few hours finding it.

I have an ASUS P5N-SLI motherboard with a AD1986A chipset that uses the snd_hda_intel module.   My case has AC '97 compliant front panel connectors instead of the Azalia connector. The sound from the rear port worked, but the front panel did not.  To fix it I followed eggdeng's suggestion and added the model option for the snd_hda_driver.  For this motherboard, adding a file with the following line to /etc/modprobe.d/ fixed the problem.

[FONT="Courier New"]options snd_hda_intel model=3stack[/FONT]

---

