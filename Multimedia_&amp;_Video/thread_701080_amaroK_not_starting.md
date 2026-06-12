---
title: "amaroK not starting"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by ben44b on 2008-02-19
My amaroK doesn't want to startup. I've tried re-installing it. I've tried starting it with amarokapp (!) At a loss...

This is what I get.

bernie@bernie-desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po

---

### Post by DNAspark99 on 2008-02-26
I just got hit with this. I recall seeing a kde-libs update a few days ago, but amarok was open and running fine until today. 

No fix yet?

---

### Post by RSiferd on 2008-02-26
My amarok isn't starting either. It was working perfectly until I updated my kde-libs.

```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po
rob@rob-laptop:~$ amarokapp
kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po

```

---

### Post by kheisler on 2008-02-26
I just got this after updating kde-libs.... anyone know of a fix?

---

### Post by RSiferd on 2008-02-26
I figured it out! Check out [this link]("http://ubuntuforums.org/showthread.php?t=695073&page=2").
I just typed:
```

sudo apt-get remove language-pack-kde-en
```
and everything worked fine!

---

### Post by DNAspark99 on 2008-02-26
> **RSiferd said:**
> I figured it out! Check out [this link]("http://ubuntuforums.org/showthread.php?t=695073&page=2").
I just typed:
```

sudo apt-get remove language-pack-kde-en
```
and everything worked fine!

BINGO! 
fantastic sir, thanks for the info! (saved me the trouble of hunting it down!)

---

### Post by rybu on 2008-02-27
I was having the same problem, but with KTorrent.  Removal of the language library as suggested above worked.

---

