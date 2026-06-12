---
title: "Problem with FFMulti Converter"
date: 2014-04-10
forum: Multimedia Software
---

### Post by Bryce_Hutchison on 2014-04-10
:) Hi all; 
I have installed FF multi converter to covert to avi xvid 640 x480  but after selecting avi when I go to the presets, the edit preset window comes up.
It appears that the are no other presets installed. 
I have made shaw that all the dependencies are there. 
Any sugestions would be appresiated. :KS

---

### Post by andrew.46 on 2014-04-10
Have you installed this from a PPA? Presets details here:

[https://github.com/Ilias95/FF-Multi-Converter/wiki/Presets](https://github.com/Ilias95/FF-Multi-Converter/wiki/Presets)

Mind you another option would be to use FFmpeg itself rather than a gui...

---

### Post by Bryce_Hutchison on 2014-04-11
Thanks for your help :KS
But by the looks of things I might have to study up on the command line option because there is no way to import the standard presets into the program.

By the way please excuse my ignorance I forgot to mension I am using Dream Studio.

Thanks again. \\:D/

---

### Post by andrew.46 on 2014-04-11
> **Bryce_Hutchison said:**
> But by the looks of things I might have to study up on the command line option because there is no way to import the standard presets into the program.

I have not installed the application but you should be able to manipulate the presets at a local level from *~/.config/ffmulticonverter/presets.xml* according to the documentation. Have a look there or even run:

```

find $HOME -iname presets.xml

```

to see if you have some local presets in place.

> By the way please excuse my ignorance I forgot to mention I am using Dream Studio.

I had not heard of this variation of Ubuntu before, looks interesting :)

---

### Post by Bryce_Hutchison on 2014-04-11
):P Thanks again for your time and effort.
Yes Dream Studio is geared totally for mutimedia production with all the usual stuff as well.

Getting back to my little hick up; I have solved all my problems with using WinFF which is the GUI front end of FFMPEG and it does every thing I wanted and very simple to use.

:D Thanks once again, :KS

---

