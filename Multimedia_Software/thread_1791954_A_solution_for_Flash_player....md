---
title: "A solution for Flash player..."
date: 2011-06-27
forum: Multimedia Software
---

### Post by Liova99 on 2011-06-27
i seach the web, the forums here, but i dont find any solution,
 ](*,)
when i wach a video on firefox or chrome, mu 2,4 dual core goes to 70-80% and the temp goes to 80C!!!! my display is Nvidia 9600M GT, my flash player version is 10.3 
i use ubuntu 11.4. 

P.s. Sory for my englesh,

---

### Post by Liova99 on 2011-06-28
i think tha nvidia driver make this problem to flash player... but i am not sure!! and a can't find any solution.. 
i can't wach any video online!!!! 
Please Hepl!!!!! :confused:

---

### Post by beew on 2011-06-28
Install flash with the flash-aid addon for Firefox, it will configure flash to use hardware decoding (VDPAU) if you have installed the NVIDIA proprietary driver (and optimize flash, clear up conflicting versions etc)

With chrome it is a bit tricky as it has it own embedded flash apparently.

If all else fail you can install the flashvideoreplacer addon for Firefox, then you don't need flash for sites like Youtube at all, this will lowers CPU usage quite a bit.

---

### Post by Liova99 on 2011-06-28
i try this, it's help with the cpu speed, but i am wored about my cpu temp... maby i mast to manualy control the fan speeds or something...

---

### Post by collisionystm on 2011-06-28
> **Liova99 said:**
> i try this, it's help with the cpu speed, but i am wored about my cpu temp... maby i mast to manualy control the fan speeds or something...


[http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/](http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/)

---

### Post by Liova99 on 2011-06-28
i try this method but when i tipe <pwmconfig> i take this ansver: < There are no pwm-capable sensor modules installed >...

---

