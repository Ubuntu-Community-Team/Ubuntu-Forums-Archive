---
title: "Where do I get soundcard drivers?"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by Permanent Beginner on 2007-09-04
The posts I've been able to find over an hour or two of searching appear to suggest that my Crystal CS4238 sound might work if I install the snd-cs4236 Linux driver.  But Google has looked everywhere for it and has found a few references to it but not it itself.

Can anyone tell me where to get it and (I'm a beginner) what to do with it when I get it?
(If you were going to just tell me to neforgulate it, I won't know what you're talking about.)

Thanks

PB

---

### Post by ddrichardson on 2007-09-04
It would be a kernel module.```
lspnp -v
```should gove you the parameters you need.

Test it with```

modprobe snd-cs4236 port=X cport=X irq=X dma1=X dma2=X
```replacing the X's with the values you got earlier.

---

### Post by max96 on 2007-09-05
> **ddrichardson said:**
> It would be a kernel module.```
lspnp -v
```should gove you the parameters you need.

Test it with```

modprobe snd-cs4236 port=X cport=X irq=X dma1=X dma2=X
```replacing the X's with the values you got earlier.

Where do you put in that code?:confused:

---

### Post by Elf on horseback on 2007-09-05
put that code in to terminal, and thats at 

applications (Top of your screen) > accessories > Terminal

---

