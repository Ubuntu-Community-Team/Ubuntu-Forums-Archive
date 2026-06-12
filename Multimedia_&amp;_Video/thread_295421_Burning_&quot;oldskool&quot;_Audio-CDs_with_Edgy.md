---
title: "Burning &quot;oldskool&quot; Audio-CDs with Edgy"
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by @Dilli on 2006-11-08
Hi everyone,
I've tried to burn a simple audio-CD with Serpentine (which was installed from default in Edgy). Everything works well: Dragged some .mp3s in their and started the burn process. No errors.

But there is a problem with playing the CD in my caraudio. It doesn't even read the CD.
In a DVD-player, I've tried, the CD just works fine and also on my computers the CD is just recognized as an normal audio-CD - playable out of the box. 
So I installed k3b and the gravething in Edgy an tried it again: Same problem! :-k 

I guess it's a problem with the way the programs are burning those audio-CDs. They create some folderstructure on the CDs which my caraudio isn't able to understand. The CDs have to be like audio-CDs in a oldskool way. Like your 20 year-old Metallica CD. Just a very simple audio-CDs with just the tracks on it.

Is there any solution for my problem? Maybe a function that can be activated in those GUI's that I haven't seen?

Greetings,
Dilli

---

### Post by angkor on 2006-11-08
Are you sure it's not just your car stereo not being able to play recordable cds?

---

### Post by @Dilli on 2006-11-08
Yes, sorry that I didn't mentioned that. I burned CDR's with Nero under Windows before. They work all fine in my car.

AND in Nero there is also a function that I can enable to burn the audio-CDs in this way.
But I don't know what this function was called...'cause I'm using Edgy now, hehe ;)

---

### Post by Teamgeist on 2006-11-08
Are you sure you actually burned it as an audio CD? I mean are the mp3s really converted into regular audio files?

Do you have the following packages installed?
```
sudo apt-get istall lame gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-good gstreamer0.10-pitfdll gstreamer0.10-ffmpeg
```

The part of the folder structure on the disc sounds kinda strange to me.

Are you already a member at [www.ubuntuusers.de](www.ubuntuusers.de) ? Great Forum from Germany. :p

---

### Post by @Dilli on 2006-11-08
> **Teamgeist said:**
> Are you sure you actually burned it as an audio CD? I mean are the mp3s really converted into regular audio files?

As I said...the CDs are recognized as normal audio CDs when I put them into my CD-Rom drive.

> **Teamgeist said:**
> Do you have the following packages installed?
```
sudo apt-get istall lame gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-good gstreamer0.10-pitfdll gstreamer0.10-ffmpeg
```

Yes, I installed them. Before I did that I got errormessages that the filetype .mp3 is not supported ;) 

> **Teamgeist said:**
> The part of the folder structure on the disc sounds kinda strange to me.

Are you already a member at [www.ubuntuusers.de](www.ubuntuusers.de) ? Great Forum from Germany. :p

I can't confirm this (because I don't get a look with Nautilus etc. on the audio CD...Sound-Juicer pops up in standard). But I've seen such structure as I burned an audio CD with Nero in the wrong way.

No, not yet...I like to torture people with my bad english, hehe :mrgreen:

---

### Post by Teamgeist on 2006-11-08
Try using another burning app.
I recommend brasero or gnomebaker.
I personally prefer brasero.

```
sudo apt-get install brasero
``` or ```
sudo apt-get install gnomebaker
```

Even though your English isn't bad at all, give [www.ubuntuusers.de](www.ubuntuusers.de) a try. Very nice people there. :)

---

### Post by @Dilli on 2006-11-08
Hmm, tried those two but doesn't work either. 
Same problem here. Playable everywere - but not in my caraudio ](*,)

When I remember right the function in Nero was called "Normalize all Audio Files" or something like this. As I said: With this function, enabled in Nero, my CDs works just perfectly in my car.


Yeah, ok I'll do it 8)

---

### Post by kubu on 2006-11-19
Hi, maybe the package "normalize-audio" can help you.
I'm not sure if it does, because i didn't try it myself, but it looks quite good and in k3b you can also find an option concerning normalize-audio.

---

### Post by rikard_grankvist on 2006-11-19
Normalizing should affect playability at all. All normalizing does is set a uniform volume for all tracks (the maximum possible without distorsion). This is done by modifying the audio file, there's no difference in the actual burning of the CD. But you can always try.

---

