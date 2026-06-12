---
title: "WinFF and non-working presets"
date: 2008-12-04
forum: Multimedia Software
---

### Post by paul.gevers on 2008-12-04
In this forum I see quite some people having problems with presets in WinFF not working. Basically there are two reasons why this could be the case:
[LIST=1]
[*]Your ffmpeg version does not support the format you try to convert to.
[*]The presets.xml file that you are currently using uses parameters that match an **other** version of ffmpeg.
[/LIST]

The way to solve the first problem is depends on which version of Ubuntu you use. Hardy users can use the ffmpeg from [Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). Intrepid users can install ubuntu-restricted-extras or kubuntu-restricted-extras or xubuntu-restricted-extras (from the multiverse repository).

The way to solve the second problem is to replace the presets.xml file found in ~/.winff/ with an other version. Updated versions can be found at [winff.org]("http://code.google.com/p/winff/downloads/list") (Extended installation instructions can be found [there]("http://code.google.com/p/winff/wiki/InstallPresetsxml")).

---

### Post by FakeOutdoorsman on 2008-12-05
If you don't want to install all of the extra junk that ubuntu-restricted-extras provides you can install just the [unstripped ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6207546&postcount=3") [link to another forum post] which will allow encoding to various restricted formats such as mp3.  The version numbers may change, so if your package manager can't find the package you'll have to search for the new name.

---

### Post by paul.gevers on 2008-12-05
> **FakeOutdoorsman said:**
> If you don't want to install all of the extra junk that ubuntu-restricted-extras provides you can install just the [unstripped ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6207546&postcount=3") [link to another forum post]...

I might be wrong, but actually I think you only need libavcodec-unstripped-51, where the number may increase in upgrades. I suggest installing the ubuntu-restricted-extras, because of this possible increase. That package *should* always depend on the correct version for the ffmpeg package in the distribution.

---

