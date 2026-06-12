---
title: "Burning ISO Image &gt;2GB to DVD"
date: 2009-07-30
forum: Multimedia Software
---

### Post by bluelamp999 on 2009-07-30
Hello friends,

I'm using DeVeDe to combine a bunch of AVIs into DVD video format (for use on a domestic DVD player).

If the resulting ISO is larger than 2GB then I'm facing problems in burning this to disc.

I know this limitation is due to ISO 9660 and, apparently, the way to go is UDF.

Can anyone advise how to burn images <4.7GB to a DVD disc in Ubuntu?

I've searched around and k3b and Nero Linux seem to be promising though I'd like to avoid Nero for the usual OSS reasons.

Any help gratefully recieved...

---

### Post by Raffles10 on 2009-07-30
What are you using to burn the iso ?

Brasero burns files larger than 2gb, it has a bug where the progress bar resets to zero, but it still burns ok.

---

### Post by bluelamp999 on 2009-07-30
Hi, thanks for replying...

Um, Brasero won't do it for me (Brasero 0.8.2 on Intrepid).

See here for bug report which replicates my situation...

[https://bugs.launchpad.net/brasero/+bug/205919](https://bugs.launchpad.net/brasero/+bug/205919)

Maybe I should update Brasero?

Thanks

---

### Post by rey1321 on 2009-07-30
Right click the ISO and then
choose write to disc option

---

### Post by bluelamp999 on 2009-07-30
> **rey1321 said:**
> Right click the ISO and then
choose write to disc option

Hey rey,

Tried that one too, it still spits the dummy at the >2GB size.

I eventually got round it by using the *growisofs* command.

---

### Post by Francewhoa on 2009-09-05
How to burn file bigger than 2GB with Ubuntu 8.04 LTS [http://ubuntuforums.org/showpost.php?p=7902011&postcount=15](http://ubuntuforums.org/showpost.php?p=7902011&postcount=15)

---

