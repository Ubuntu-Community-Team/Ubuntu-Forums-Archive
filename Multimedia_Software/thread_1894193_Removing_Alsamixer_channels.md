---
title: "Removing Alsamixer channels"
date: 2011-12-12
forum: Multimedia Software
---

### Post by andyjjones on 2011-12-12
Hi folks,

I've been trying very hard to remove some unwanted channels from 'Alsamixer'.  For example, in the below screenshot, I would like to remove all "Earpiece" channels.

[IMG]http://i11.photobucket.com/albums/a199/bumclouds/alsamixer-sample.png[/IMG]

I have identified what I think is the piece of code responsible for creating those mixer channels;  (dots indicate where other code has been cut out)

```
        
static const struct snd_soc_dapm_widget twl4030_dapm_widgets[] = {
 ...
SND_SOC_DAPM_MIXER("Earpiece Mixer", SND_SOC_NOPM, 0, 0,
                        &twl4030_dapm_earpiece_controls[0],
                 ARRAY_SIZE(twl4030_dapm_earpiece_controls)),
...
};

```

Apart from exploring the array and removing that particular element, is there an easier way?

- Andrew

---

### Post by andyjjones on 2011-12-20
**bump** Sorry to bump.  But it's been a long time and I still cannot solve my problem :(!!

---

### Post by MoreOrLess on 2011-12-20
It would probably be easier to use a GUI mixer with the capability of hiding unwanted channels rather than hacking alsamixer code...

---

