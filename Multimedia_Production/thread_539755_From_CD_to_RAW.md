---
title: "From CD to RAW"
date: 2007-08-31
forum: Multimedia Production
---

### Post by Aleksandersen on 2007-08-31
Hi,

How can I copy songs from a regular audio compact disk to .raw audio?

---

### Post by distort on 2007-09-01
You can use cdparanoia to grab tracks from an audio cd.

cdparanoia -B

will grab all the tracks from the audio cd to one wav file per track.

Maybe you'll have to specify your cd-rom device as an option.

I think you can make it output raw with some command line switch, the command would be

cdparanoia --output-raw -B

but I didn't test it.

If it doesn't work, then use sox to convert wav to raw or another format sox supports.
But turn down the volume of your speakers before playing back the resulting files, because if something went wrong you'll only get harsh
noise that could damage your speakers.

---

