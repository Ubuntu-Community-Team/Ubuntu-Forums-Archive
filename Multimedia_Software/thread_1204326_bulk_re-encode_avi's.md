---
title: "bulk re-encode avi's"
date: 2009-07-04
forum: Multimedia Software
---

### Post by toddr on 2009-07-04
Hi
Does anyone know of a way to re-encode a directory full of .avi (xvid) files? I have about 80 or so videos that all work on my computer but do not on my Popcorn Hour. I found that if I re-encode them with avidemux, they work flawlessly. The only problem with doing it this way is I have to do them one at a time. I don't need a gui, command line is fine. Thanks

Todd

---

### Post by toddr on 2009-07-07
(bump)

---

### Post by viper8 on 2009-10-24
> **toddr said:**
> (bump)

in general, you can easily repeat commands using:

for i in *.avi; do avidemux $i -other -options; done

---

### Post by vinutux on 2009-10-25
TRy handbrake cli version | Help is here [http://trac.handbrake.fr/wiki/CLIGuide]("http://trac.handbrake.fr/wiki/CLIGuide")

---

