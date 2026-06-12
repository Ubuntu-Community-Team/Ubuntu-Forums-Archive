---
title: "WinFF is a PAIN....help!"
date: 2008-09-29
forum: Multimedia Software
---

### Post by MaverickCoast on 2008-09-29
along with other programs I have tried to use to convert .flv files.

I have tried to convert .flv to .wmv and have tried to convert .flv to .avi AND NEITHER works, keep getting error messages.

Have read EXTENSIVELY on how to install it, where to install it from, what to do, what not to do! :(

Here is the error message:

"Error while opening codec for output stream #0,0 - maybe incorrect parameters such as bit_rate, rate, width, or height"

It sounds as if you manually have to enter those settings under advanced. What settings do I enter or where do I find the settings that I need to use?

Thanks for any help!!!!

Mav

---

### Post by FakeOutdoorsman on 2008-09-29
WinFF presets may not work depending on how old your version of ffmpeg is.  This is because ffmpeg's encoding options often change names between revisions.  What is the output of "ffmpeg -version"?  Which WinFF settings or presets are you using?

---

### Post by MaverickCoast on 2008-09-29
> **FakeOutdoorsman said:**
> WinFF presets may not work depending on how old your version of ffmpeg is.  This is because ffmpeg's encoding options often change names between revisions.  What is the output of "ffmpeg -version"?  Which WinFF settings or presets are you using?

- Don't know version of ffmpeg, but I installed it via repositories through the terminal.

- I have not entered OR changed any settings or presets.

---

