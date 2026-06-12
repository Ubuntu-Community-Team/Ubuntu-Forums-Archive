---
title: "Can't play WMV filez..."
date: 2010-10-18
forum: Multimedia Software
---

### Post by figamaster on 2010-10-18
[I]Real newbie in ubuntu - can't play WMV files.
Installed VLC player - didn't help.
If anyone know an easy way...
TNX


[/I]

---

### Post by mstjohn1974 on 2010-10-19
follow the instructions on this page and it should solve all issues.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by perspectoff on 2010-10-19
Make sure you have the restricted extras package installed. Either install ubuntu-restricted-extras (or kubuntu-restricted-extras) from a Package Manager (Synaptic or KPackageKit), or install from the CLI (Terminal or Konsole) using, for example:

 sudo apt-get install ubuntu-restricted-extras

You should then associate WMVs with VLC.

(Download and) save a WMV file, then open it with a right-click.

Open with... -> Other... -> Highlight: "VLC Media player" -> Check: "Remember application association for this type of file"

---

