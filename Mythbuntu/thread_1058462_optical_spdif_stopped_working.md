---
title: "optical spdif stopped working"
date: 2009-02-02
forum: Mythbuntu
---

### Post by itlarson on 2009-02-02
My optical spdif out has stopped working.  For all applications, not just mythtv.  Analog output still works for other apps, and for mythtv it works if if I uncheck spdif pasthrough.   This snippet from the mythtfrontend log is as close as I have gotten to a clue:

2009-02-02 01:51:58.279 AFD: codec AC3 has 6 channels
2009-02-02 01:51:58.279 AFD: Opened codec 0x99a20a0, id(AC3) type(Audio)
2009-02-02 01:51:58.279 AFD: codec AC3 has 1 channels
2009-02-02 01:51:58.280 AFD: Opened codec 0x9e7d6e0, id(AC3) type(Audio)
2009-02-02 01:51:58.415 Opening audio device 'spdif'. ch 6(2) sr 48000
2009-02-02 01:51:58.415 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2009-02-02 01:51:58.416 AudioOutput Error: Channels count (6) not available: Invalid argument
2009-02-02 01:51:58.416 AudioOutput Error: Unable to set ALSA parameters
2009-02-02 01:51:58.416 NVP: Disabling Audio, reason is: Unable to set ALSA parameters

Can Anyone help?

---

### Post by itlarson on 2009-02-02
Solved: [http://ubuntuforums.org/showthread.php?p=5516332#post5516332](http://ubuntuforums.org/showthread.php?p=5516332#post5516332)  had the answer.  It was just settings.  Not sure how they got changed.

---

