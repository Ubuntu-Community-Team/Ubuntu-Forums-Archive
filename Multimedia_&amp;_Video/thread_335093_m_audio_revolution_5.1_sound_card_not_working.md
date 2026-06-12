---
title: "m audio revolution 5.1 sound card not working"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by rbprogrammer on 2007-01-09
ok, so i have a sound card (m audio revolution 5.1) and i dont get any sound.  i tried searching the forums, but it seems like other people with the card get static as audio output.  but i get nothing.  does anyone know how to fix this?

when doing [lspci] i get (if it helps):
```

...
01:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
...

```

i also heard that using the OSS sound drivers would work, *rather than using alsa*?  but even then, i dont know how to switch to OSS and make them my default.  if someone knows how to do that, it would also be greatly appreciated.

i heard this from: [http://ubuntuforums.org/archive/index.php/t-179148.html](http://ubuntuforums.org/archive/index.php/t-179148.html)

---

### Post by rbprogrammer on 2007-01-09
i tried this using alsamixergui, but that still doesnt work :(  .......

---

### Post by rbprogrammer on 2007-01-11
bump

---

### Post by cylon359 on 2007-01-13
I have one of these too, and it works just fine with edgy, except that after boot, the left channel has no sound until the volume is adjusted...

$ lspci | grep VIA
07:00.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

---

### Post by rbprogrammer on 2007-01-14
did you do anything configuration wise to get it to work like that?  because mine does not have any sound.  i even did a fresh install on Kubuntu and i had no luck.  then i installed all the most recent updates and still no luck.

---

### Post by cylon359 on 2007-01-14
Mine worked out of the box... hmmm... if you try the command line alsamixer program, what are you settings to "H/W", "H/W 1", and so on... mine have to be set to "PCM Out" otherwise I don't get sound.

---

### Post by cylon359 on 2007-01-14
"what are you settings to" should read "what are your settings for", sorry.

---

### Post by rbprogrammer on 2007-01-20
i set the all the [H/W]'s to [PCM Out], then restarted the computer, i still have not gotten sound to work through the card.  this is my whole [alsamixer -c 1] settings:

---

### Post by sgx on 2007-01-20
> **rbprogrammer said:**
> i set the all the [H/W]'s to [PCM Out], then restarted the computer, i still have not gotten sound to work through the card.  this is my whole [alsamixer -c 1] settings:
First, install envy24control, its designed for maudio products. If after a reboot, you can't get sound from the mixer in envy24control. reboot with the unit unplugged, then run envy24control again from the shell, then plug in the maudio box, and look for signs of life. If still no tunes, try your bios settings, and shutdown plug-n-play, acpi, onboard audio system, networking, etc, hope this helps...

---

### Post by cylon359 on 2007-01-24
envy24control doesn't work with the revolution 5.1... it's a ice1724 and envycontrol wants the ice1712 (or whatever it is)

---

### Post by cylon359 on 2007-01-24
Oh, you're not trying to use the digital audio out, are you?  I don't think that part works...

---

### Post by miceagol on 2007-01-26
> **cylon359 said:**
> Oh, you're not trying to use the digital audio out, are you?  I don't think that part works...

Can anybody confirm this? I thought of buying this card, but now I might not after all.

---

### Post by rbprogrammer on 2007-02-02
> **cylon359 said:**
>  ... envy24control doesn't work with the revolution 5.1... it's a ice1724 and envycontrol wants the ice1712 (or whatever it is)
sorry, i'm just alittle confused, what do you mean? should i install envy24control?

and if i should, where do i get it? i cant find it adept.  i have the multiverse and universe enabled.......

---

### Post by sgx on 2007-02-03
> **rbprogrammer said:**
> sorry, i'm just alittle confused, what do you mean? should i install envy24control?

and if i should, where do i get it? i cant find it adept.  i have the multiverse and universe enabled.......

In the past, it has been part of alsa-utils. Might be there still...on another note, the 'smart' installation
system would be worth looking into, for times when apt is just too limited. About 30 minutes of reading
and configuring for slow perpetual newbies like myself...probably much less for most folks!

---

### Post by rbprogrammer on 2007-02-04
i already have alsa-utils installed, but i still cannot find the envy program.....

---

