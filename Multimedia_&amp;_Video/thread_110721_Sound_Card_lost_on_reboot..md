---
title: "Sound Card lost on reboot."
date: 2005-12-31
forum: Multimedia &amp; Video
---

### Post by jacrider on 2005-12-31
I have an older dell computer with an onboard sound card.

I have found that the following command will activate it:

sudo modprobe snd-cs4236

My questions is how to make this happen on start-up.  As you can tell, I am new to ubuntu, so any help is greatly appreciated.

Thansk.

---

### Post by jacrider on 2006-01-01
I have managed to solve this problem.

I modified my /etc/modules file and appended "snd-cs4236" to the end of the list and now everything works after booting.  

Found this on an old thread in this forum.  Once again, this forum has been very helpful.

---

### Post by Pulka on 2007-11-13
That happens to me, too. 

How do I find what to put in /etc/modules file?

Thanks

---

