---
title: "Equalizer for linux"
date: 2016-11-30
forum: Multimedia Software
---

### Post by recalcitrant on 2016-11-30
Hello

I am looking for a Linux system equalizer. There used to be *pulseaudio equalizer* but it is not developed any more and I can't find it in Lubuntu Software Centre (for safety reasons I don't install anything out of it). [B]Is there any?
[/B]I tired to find the answer on the internet but posts I found were out of date, from 2008 for instance, so I am asking now. I know there are  application specific equalizers. In video programs. But I need one for general use - for system. For youtube for instance.

thx

---

### Post by Yellow Pasque on 2016-11-30
I just fired up my Ubuntu 16.04 VM and the equalizer module is included in the pulseaudio package. Check:
```
ls /usr/lib/pulse*/modules | grep equal
```

---

### Post by ajgreeny on 2016-11-30
Try this site which has a PPA for the equaliser.  It is no longer supported but still apparently works according to others; I have not bothered as my hifi amp works even better than any equaliser could.
[http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html)

---

### Post by recalcitrant on 2016-11-30
@Temujin

I have Lubuntu 16.04. Pulse audio is not installed on my machine. How ever the line provided returns:
module-equalizer-sink.so

How am I supposed to start the equalizer?

thx

---

### Post by Yellow Pasque on 2016-11-30
Yeah, I just realized that Ubuntu doesn't ship the qpaeq GUI to control the equalizer (though it looks like they will in Ubuntu 17.04).
Does Lubuntu not use pulseaudio?

---

### Post by recalcitrant on 2016-12-01
So do I have to install soft out of repository to have equalizer? The only answer is from [**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747") (link from you is 3 years old). I have lubuntu 16.04. Any other solutions, more decent?

---

### Post by Yellow Pasque on 2016-12-02
> **recalcitrant said:**
> So do I have to install soft out of repository to have equalizer?
Yes. Ubuntu can't package every piece of software under the sun and have it in their repo. If you don't trust PPA's, install from pulseaudio's source directly as described here (skipping Step1):
[http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)
You're installing one open source script directly from pulseaudio (the same file Ubuntu is going to put in 17.04). If that's not good enough for you... *shrug*

---

