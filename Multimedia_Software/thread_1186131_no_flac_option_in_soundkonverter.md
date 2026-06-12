---
title: "no flac option in soundkonverter"
date: 2009-06-13
forum: Multimedia Software
---

### Post by nafihsus on 2009-06-13
I am using soundconverter for ripping my CD collection on two different PCs (both Hardy). No problems on one but the other one does not offer the option "flac" when I want to convert lossless, only wav and wv. Looking in the list of plugins FLAC v. 301 is listed as "should be shipped with my distribution".  

Any idea?

---

### Post by hayden92 on 2009-06-13
I'm not really sure what could be causing this problem. Have you tried reinstalling the program?

---

### Post by mc4man on 2009-06-13
Install flac (soundkonverter uses flac, not libflac, faac, not libfaac, ect. 

To ck. open sk's setting and look in Environment (note sk. usually needs to be restarted after you install something or make setting's changes

---

### Post by nafihsus on 2009-06-13
Thx. Installing flac solved it. I had in mind that flac would be in the standard distro.

---

### Post by mc4man on 2009-06-13
while with flac it won't matter if ever using other formats also ck. in the 'backends' to see if there is a 'better' encoder, decoder, ripper available (green vs yellow or red

---

### Post by nafihsus on 2009-06-13
Celebrated too early. Now I can select flac, sk recognizes CD but won't rip. Remains in state "waiting" forever.

---

### Post by mc4man on 2009-06-13
Never used sk for ripping but this is what seems to happen (in gnome)

I only have cdparanoia installed so that's what must be set in backends and it does work.

What happens though is when you open the settings -> configure soundkonverter **for anything, it then reverts the ripper back to kio_audiocd even if you don't open backends.**

So every time you open settings you'd need to reset the ripper back to cdparanoia before exiting.

If you open ~/.kde/share/config/soundkonverterrc you can see what's set and how it changes when opening the settings menu (**for anything**

---

### Post by nafihsus on 2009-06-20
:D Thank you for the hint.
Works fine again.

---

### Post by mc4man on 2009-06-20
I also noticed that the other possible ripper - cdda2wav,  isn't to be found.
Turns out it's included now in the icedax package.

cdparanoia works fine here, just thought I'd mention

---

