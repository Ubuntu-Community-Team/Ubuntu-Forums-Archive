---
title: "Sigmatel Audio Issue"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by brandoncolorado on 2007-01-28
I have HDA-Intel Audio card on my laptop.  Codec Sigmatel Stac92xx.  I have no sound output.  I have searched numerous forums and posts without a solution.  Also, there is a bug listing at ALSA with no answer since August of 2006.  Am I out of luck?

---

### Post by eggdeng on 2007-01-29
Try 
```
sudo gedit /etc/modprobe.d/options
```

add the line

```
options snd-hda-intel probe_mask=1
```

save, and reboot. Let me know if it works as I'm trying to put together a sort of how-to for snd_intel_hda problems.

---

### Post by brandoncolorado on 2007-01-30
> **eggdeng said:**
> Try 
```
sudo gedit /etc/modprobe.d/options
```

add the line

```
options snd-hda-intel probe_mask=1
```

save, and reboot. Let me know if it works as I'm trying to put together a sort of how-to for snd_intel_hda problems.

No luck, and I used the sound tests for all of the different choices - sigmatel stac92xx digital, analog, oss, etc.

---

### Post by eggdeng on 2007-01-30
A guy in this thread, [http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200](http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200) , seems to have got the same card working adding 
```
options snd-hda-intel model=ref
``` 
to the file I mentioned earlier.
You will need to reboot for changes to take effect.

---

### Post by brandoncolorado on 2007-01-30
Nope, same problem, no sound.  I wonder if the Gateway is different than the Dell version?

No errors when I test the different devices, but the OSS and the Stac92xx give this error.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.

---

### Post by eggdeng on 2007-01-30
I have a note for a Gateway with a Sigmatel card which runs as follows:

```
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```

I think it came from [http://ubuntuforums.org/showthread.php?t=251877&page=2&highlight=Intel+HDA](http://ubuntuforums.org/showthread.php?t=251877&page=2&highlight=Intel+HDA), post #19.

---

### Post by brandoncolorado on 2007-02-03
Same problem and no error message.  Thanks for the help though.  :(

---

### Post by brandoncolorado on 2007-03-03
Any other ideas I can try?

---

### Post by eggdeng on 2007-03-04
You could try fooling around with edits like options ```
snd-hda-intel model=gateway
``` or ```
snd-hda-intel model=gateway-laptop
``` More suggestions at
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)
You could also try updating / reinstalling alsa. How-to at [http://ubuntuforums.org/showthread.p...ghlight=alc260](http://ubuntuforums.org/showthread.p...ghlight=alc260).

---

### Post by Z3PX on 2007-03-09
> **eggdeng said:**
> A guy in this thread, [http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200](http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200) , seems to have got the same card working adding 
```
options snd-hda-intel model=ref
``` 
to the file I mentioned earlier.
You will need to reboot for changes to take effect.

This worked for me on this chipset. I'm running Dell dimension 5150 by the way.

---

### Post by brandoncolorado on 2007-03-10
> **Z3PX said:**
> This worked for me on this chipset. I'm running Dell dimension 5150 by the way.

Thanks for the reply.

I tried that one a while back and no go.  It looks like (after talking to the maintainer for ALSA) that this is a real bug that involves some coding.  Looks like all of us are going to have to wait (those of us with the Gateway MX341* and the Sigmatel Stac 9200).

:(

---

### Post by DaMasta on 2007-03-12
Try this: [http://www.payn3.com/comments.php?a=6](http://www.payn3.com/comments.php?a=6)

---

### Post by brandoncolorado on 2007-03-18
Thanks for the link.  Unfortunately, that trick doesn't work with the Gateways.  I don't know what is different about our systems, but unfortunately that trick doesn't work.

---

### Post by BeepAU on 2007-03-26
Sorry to bring back an old thread, but I have the same sound card and the same problem. I tried installing OSS and was able to get very low sound from my headphones as opposed to nothing with a couple of weeks of trying with ALSA. I wanna keep trying this route. How can I alter OSS to get sound working well? That is, from both my speakers and headphone jack at a good volume.

---

