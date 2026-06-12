---
title: "sound thrashing when performing tasks"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by ministoat on 2007-09-04
im getting sound thrashing whenever i run a program, loads a new webpage etc. 

i'm using an maudio delta 66, on alsa drivers afaik, don't rly know what to do :confused:

---

### Post by loell on 2007-09-04
does this happen even if you don't play music in the background?

---

### Post by ministoat on 2007-09-04
pretty much only when there's music going on..i don't know if this is logical but isn't it still  happening when there's not music on but there's just no way of hearing it?

it also happens when i run WoW in wine too..jitters and cracks.

---

### Post by loell on 2007-09-04
my hunch is, you are experiencing an age old problem in Linux, this is probably because of the scheduler, see when theres too much task going on in the background it could skip the background sound you're playing. or in your case sound thrashing?

this issue , is somewhat political and technical, i guess

[http://apcmag.com/6759/interview_with_con_kolivas_part_1_computing_is_boring]("http://apcmag.com/6759/interview_with_con_kolivas_part_1_computing_is_boring")

> f we numerically quantify it with all the known measurable quantities, performance is better than ever. **Yet all it took was to start up an audio application and wonder why on earth if you breathed on it the audio would skip. Skip!** Jigabazillion bagigamaherz of CPU and we couldn't play audio?

---

### Post by ministoat on 2007-09-04
"sounds" like a common problem :P

from his interview it seems that it's resolved though - is it worth running his kernel patch on this page [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/) ?

i'm not sure where to find out what kernel version i'm using

---

### Post by loell on 2007-09-04
well, you could wait for ubuntu hardy heron ;)

i think by that time then. 2.6.23 will be ubuntu's kernel, which has CFS (completely fair scheduler) 

you can find out what kernel you are running by invoking the command

```
uname -a
```

---

### Post by ministoat on 2007-09-04
thanks - so feisty uses 2.6.00 according to what i get back from that command

i'm guess it's not a simple thing to update the kernel with the script?  i'm like 3days into ubuntu use and i don't wana f'ck it up (again)

---

### Post by ministoat on 2007-09-05
bump ^^

---

### Post by CnlPepper on 2007-09-13
I also had problems with audio skipping etc... the solution was to install a version of the feisty kernel patched with the Completely Fair Scheduler. Instructions are here:

[http://ubuntuforums.org/showthread.php?p=3318457](http://ubuntuforums.org/showthread.php?p=3318457)

It works exceptionally well, generally improves system responsivity and has completely fixed the audio issues.

---

