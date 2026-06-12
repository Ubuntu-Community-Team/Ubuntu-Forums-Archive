---
title: "sound problem for Skype and Firefox+Flash in 10.04"
date: 2010-05-01
forum: Multimedia Software
---

### Post by japs_it88 on 2010-05-01
Hello everybody,
I just freshly installed 10.04 and I found that the sound doesn't work with Firefox and with Skype2.1.0.81 (though I get perfect output in Amarok and I can record from the mic just fine using QARecord).

I have an Intel ALC880 integrated card and neither issue was present in 9.10.

Has anybody figured out a solution for either or both problems?
Thanks in advance,
j

---

### Post by andey on 2010-05-01
exact same problem, no sound in anything but amorok and the bootup sound

---

### Post by Daedal on 2010-05-01
just amarok and the login sound for me as well.

scratch that. sound works just had to open the mixer and turn up the PCM bar.

---

### Post by andey on 2010-05-01
> **Daedal said:**
> just amarok and the login sound for me as well.

scratch that. sound works just had to open the mixer and turn up the PCM bar.


great that works perfectly, i never knew the PCM bar also needed to be turned up

---

### Post by japs_it88 on 2010-05-01
Thanks man!

---

### Post by xcorsary on 2010-05-02
Hi, yes i got the PCM issue solved, but now i check that the incorporated MICROPHONE doesn't work... and I don't know what it is... I use a lenovo thinkpad edge...?

any ideas?

---

### Post by N.Scotian on 2010-05-02
Thanks Daedal, this was my problem too. Turned on PCM. Now its fixed.

---

### Post by mlitty on 2010-06-15
Amazing.  I've looked for over and hour for libs to install, packages to downgrade, etc.  All I had to do was turn up the PCM.  
*grin*

Very nice.  Thanks.

---

### Post by taylormc on 2010-09-17
xcorsary, bit of a late reply, I'm afraid... I had the same problem, and eventually cured it by setting the Digital channel level up in Kmix. Don't ask me why, it's a bit of a mystery to me :-)

---

