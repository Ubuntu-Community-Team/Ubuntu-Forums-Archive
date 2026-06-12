---
title: "flash and other sound interference"
date: 2008-09-06
forum: Multimedia Software
---

### Post by b4rt on 2008-09-06
Hi,

I have the alsa-oss package installed, but still, i cannot make multiple programs make use of the sound card at the same time...

Is there something else I need to configure?

ubuntu 8.10, but same problem on all previous versions

Thanks in advance,

Bart

---

### Post by ~LoKe on 2008-09-06
That's an ongoing problem that, as far as I know, is only really solved with PulseAudio at the moment.

---

### Post by mrblue182 on 2008-09-06
I need help to, thank in advanced as well.

---

### Post by b4rt on 2008-09-06
Thanks for letting me know guys,

Does anyone have an idea when this is going to be fixed and integrated into ubuntu?

thanks

---

### Post by wolfen69 on 2008-09-06
[this]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulse+audio") thread should help. also, do ```
sudo apt-get install libflashsupport
``` for good measure.

---

### Post by b4rt on 2008-09-07
thanks a lot! installing the libflashsupport package worked!

greetz,

Bart

---

