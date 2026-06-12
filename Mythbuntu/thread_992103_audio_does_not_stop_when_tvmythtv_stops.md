---
title: "audio does not stop when tv/mythtv stops"
date: 2008-11-24
forum: Mythbuntu
---

### Post by Narai on 2008-11-24
Hi there,

I'm pretty new to Mythbuntu and Linux in general.
Did not find any problems related to my one on google so I guess it's kind of unique.
I use a Pinnacle PCTV Vision Pro tuner and a Terratec Aureon 7.1 PCI as sound device. The machine is a backend/frontend installation of Mythbuntu 8.10 (fully updated).
My problem is that if I start viewing TV once the sound won't stop even if I close the frontend. It just goes on and on and on. Only solution for now is to mute Line In. Pretty annoying -.-

I think one possible way to solve this is to automatically mute and unmute Line In when viewing TV since it's not used anyway besides for that. However, I have no clue how to do that :(

Hope someone can help
Fabian

---

### Post by Narai on 2008-11-25
Was it that stupid to ask?

Anyway, I found something that could be modified to solve my problem but I don't know how to do that since I start the TV through the Mythbuntu frontend.

[http://ubuntuforums.org/showthread.php?t=7754](http://ubuntuforums.org/showthread.php?t=7754)

> Thanks entirely to the support of Rich Duzenbury, this has now been achieved. The solution is obvious to any of you beyond n00b status, but for those like me here's how to do it:

1> Install aumix (a small soundcard mixer)
2> Make the following script, ensuring that the file has execute permissions:
#!/bin/sh
aumix -l 100
tvtime -t /tmp/TV.xml
aumix -l 0
3> When you want to start TVtme, execute the script rather than the application directly. In Gnome you can do this by right-clicking your TVtime icon, choosing 'properties' and changing the command (to for example in my case: '/usr/local/share/scripts/tvtime.sh')

Finally this type of solution should work regardless of which TV app you use, provided the audio signal goes into your sound card via the 'line' channel.

Thanks again Rich!

---

### Post by fishbulb1022 on 2008-12-27
I had problems with this using tvtime (as well as many others). The solution I posted may be similar to one with mythtv. its posted here [http://ubuntuforums.org/showthread.php?p=6445498#post6445498]("http://ubuntuforums.org/showthread.php?p=6445498#post6445498")

you'll need to replace anything that says tvtime with mythtv, but I would think it would work about the same.

---

