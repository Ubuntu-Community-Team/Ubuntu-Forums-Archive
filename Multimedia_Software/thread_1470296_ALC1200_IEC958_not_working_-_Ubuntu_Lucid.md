---
title: "ALC1200 IEC958 not working - Ubuntu Lucid"
date: 2010-05-02
forum: Multimedia Software
---

### Post by dado483 on 2010-05-02
Hi all,

i have an Asus P5Q with ALC1200 integrated sound card.
I've upgraded today my system from Ubuntu Hardy 8.04 to Ubuntu Lucid 10.04. In Hardy all was working ok, but in Lucid i have no sound, SPDIF (IEC958) seem not working.

Any help is appreciated.

Davide

---

### Post by dado483 on 2010-05-04
No one has the same problem?

---

### Post by plutoprime on 2010-05-04
I have an asus p5B Plus and I think I have the same issue. I created another thread and so far I have found no solutions... During playback I see the volume meter bouncing around like it detects the sound but nothing comes out of my speakers :(

---

### Post by dado483 on 2010-05-06
I've try to google this problem, but seem no one have find a solution. Is maybe necessary open an official bug report for this?

---

### Post by Wandang on 2010-05-10
hi buddies.

i have a alc1200 soundcard too.
had nearly the same issues (could only hear sound throu headset)

try this:
[http://ubuntuforums.org/showpost.php?p=7279149&postcount=1](http://ubuntuforums.org/showpost.php?p=7279149&postcount=1)

that didnt work for me, but if u write:
```
options snd-hda-intel model=targa-dig
```
(credits to 	 																											 									[ 										ghostrider87]("http://www.ubuntu-forum.de/index.php?page=User&userID=33655") from ubuntu-forum.de)
instead it could work (it did for me)

the subwoofer still wont work, but its a start^^
greetings

---

### Post by dado483 on 2010-05-11
> **Wandang said:**
> hi buddies.

```
options snd-hda-intel model=targa-dig
```



Hi all,
i've tried the solution proposed, initially seem work but after a reboot it don't work again.
I think that isn't a solution for the problem....
For me is a pulseaudio problem, but is only a my idea.

Waiting for other solutions....
Thanks

---

### Post by Wandang on 2010-05-11
hmm
```
options snd-hda-intel model=targa-2ch-dig

```

did also work.. maybe that will permanently work...

if not i dont have an idea...
u should close all audioprograms while doing this(based on my feelings).

greetz

---

### Post by dado483 on 2010-05-13
> **Wandang said:**
> 
```
options snd-hda-intel model=targa-2ch-dig

```

did also work.. maybe that will permanently work...


Where have you put this code?
In a new file called /etc/modprobe.d/hda_intel.conf or in the /etc/modprobe.d/alsa_base.conf ?

This evening i'll try this new code, the i'll post a report.
Thanks

---

### Post by dado483 on 2010-05-13
I've tried this last solution, but for me is not working.

Waiting for other solutions....

Thanks

---

### Post by Wandang on 2010-05-14
u need to create this file: 
sudo gedit /etc/modprobe.d/hda_intel.conf

and put this into it:
options snd-hda-intel model=targa-2ch-dig

but as u said it didnt work for u.. too bad :/

---

