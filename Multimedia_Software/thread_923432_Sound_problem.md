---
title: "Sound problem"
date: 2008-09-18
forum: Multimedia Software
---

### Post by rohan_morajkar on 2008-09-18
I've just installed Hardy Hadron Ubuntu Ultimate 1.8 as a secondary OS.
I've a Sony VAIO VGN-FZ27G and the problem I'm facing is whenever I plugin an external speaker/headphone sound doesnt come through the external device but continues coming through the on board speakers. There is also no option called switch available in the volume control which is there inmy frnd's lappy. My sound card is Sigmatel high definition audio codec. Pls help me.

---

### Post by S15_88 on 2008-09-18
try opening the terminal and typing: alsamixer
and see if anything is muted.  post back with your results

Alain

---

### Post by Curlydave on 2008-09-18
Very common problem, I forgot how to fix it. A way around it is to disable your onboard sound in the BIOS settings, and Ubuntu will then use your sound card.

Ubuntu devs: Please add in a GUI device switcher that's easy to get to in the next version. :) This has been needed for a while.

---

### Post by markbuntu on 2008-09-18
If you are having problems with your HDA card/chip you should look here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

