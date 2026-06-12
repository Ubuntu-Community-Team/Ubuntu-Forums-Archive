---
title: "[SOLVED] sound puzzle involving flash, skype, amarok, vlc, totem,..."
date: 2008-09-17
forum: Multimedia Software
---

### Post by seul on 2008-09-17
I have a sound puzzle to solve and I find it hard to reproduce. I still hope the informations I can provide will be sufficient to narrow the problem down. 

I have sound in some applications and no sound in others. Now the puzzling thing is, that the members of the sound-group and the no-sound-group constantly change, so I don't really know where to start looking.

Sometimes Amarok and Kaffeine play, I can hear sound of .mp3, .flv and .vob files in VLC. But then I don't get the »ping« of a new chat message in Gmail and Skype says there is a sound problem.

At other times Amarok and Kaffeine hang and then crash. VLC progression indicator is moving forwards but I have no sound. But then I could hear the gmail ping. I couldn't hear sound of .flv in VLC but could hear sound on a random youtube video.

At the moment the sound-group are:
- skype (in & out) 
- rhythmbox
- totem (.vob, .mp3, .flv)

No sound members are:
- flash in Firefox (loads but hangs)
- Amarok (crash)
- Kaffeine (crash)
- VLC (picture is fine, though)

An hour ago Amarok played just fine. I hit pause, had a bite to eat and when I came back it had crashed. No sleep, no restart, no logout in between. Sometimes it crashes right from the beginning, sometimes not.

What can I do to find the root of the problem? Thanks very much.

---

### Post by cozmicharlie on 2008-09-17
Try this fix

[http://www.ubuntugeek.com/pulseaudio-fixes-system-wide-equalizer-support-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/pulseaudio-fixes-system-wide-equalizer-support-in-ubuntu-804-hardy-heron.html)

---

### Post by seul on 2008-09-17
Thanks very much for your quick reply. On
```
sudo aptitude remove nspluginwrapper
```
I get
```
Couldn't find any package whose name or description matched "nspluginwrapper"
```
And now loads of TeX packages are being removed:

```
The following packages are unused and will be REMOVED:
  cm-super cm-super-minimal context feynmf lcdf-typetools libkpathsea-dev libmono-cairo2.0-cil
  musixlyr musixtex musixtex-slurps pfb2t1c2pfb preview-latex-style psutils t1utils tex4ht
  tex4ht-common texinfo texlive-bibtex-extra texlive-games texlive-generic-extra
  texlive-generic-recommended texlive-humanities texlive-humanities-doc texlive-lang-german
  texlive-lang-greek texlive-lang-hebrew texlive-lang-latin texlive-lang-ukenglish
  texlive-latex-extra texlive-latex-extra-doc texlive-latex3 texlive-math-extra
  texlive-metapost texlive-metapost-doc texlive-music texlive-omega texlive-pictures
  texlive-pictures-doc texlive-plain-extra texlive-pstricks texlive-pstricks-doc
  texlive-publishers texlive-publishers-doc texlive-science texlive-science-doc texlive-xetex

```

Is that right?

---

### Post by seul on 2008-09-17
Alright, that seemed to have done the trick. Thanks a million.

Only the removal of the TeX packages seems odd.

---

