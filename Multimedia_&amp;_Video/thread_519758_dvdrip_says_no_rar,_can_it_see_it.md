---
title: "dvdrip says no rar, can it see it?"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by howardde on 2007-08-07
hi,
Whilst trying to set up dvdrip, the preferences dialogue that autoruns gives me some unmet dependencies.
Adept fixed the first few no problem, but this one:

rar command (for vobsub compression): rar-2.80 not found : NOT Ok

...persists, even after installing unrar and unrar-free, again via adept.

Can anyone shed some light on this please? can dvdrip not find the program?

Cheers,
Howard.

---

### Post by tbroderick on 2007-08-07
Try installing rar not unrar.

---

### Post by howardde on 2007-08-07
I've got rar.

---

### Post by franny on 2007-08-16
either no one cares, or if they do, they're busy caring somewhere else

i've got the same issue - anyone?

just curious...dvdrips, just apparently is oblivious to rar's being on my computer

---

### Post by nickmcg on 2007-08-20
I just came across this problem, and it seems to be fixed by Edit->Preferences and change the command line from rar-2.80 to rar.

(I still haven't managed to rip a DVD yet tho')

---

### Post by anindya_m on 2008-02-20
Hi. Changing the executable will not solve the problem. The compressed subtitles have to use the old rar 2.7 package; rar 3.0 is not supported on DVD's. The dvdrip code checks specifically for the old version (see, for example, the file /usr/share/perl5/Video/DVDRip/Depend.pm line 164).

It is simple to install rar 2.71. It is available [[COLOR="Blue"]_here_[/COLOR]]("http://www.exit1.org/dvdrip/contrib/rarlnx271.sfx.bin"). This link is on dvdrip's homepage. Just run this self-extracting archive:
```

chmod +x rarlnx271.sfx.bin
./rarlnx271.sfx.bin

```
This will create a rar directory. It's best to put this in /usr/local and create symlinks in /usr/local/bin:
```

sudo chown -R root:root rar
sudo mv rar /usr/local/rar2.71
cd /usr/local/bin
ln -s /usr/local/rar2.71/rar .
ln -s /usr/local/rar2.71/unrar .

```
After this dvdrip should find the rar executable in /usr/local/bin and accept it. Hope this helps.

---

