---
title: "Onboard video card not listed"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by tonyhawz on 2007-11-28
I have an onboard graphics card, I think its via unichrome , that is not listed by typing lspci.
The thing is that I want to enable dual head with xinerama and I cant get the hardware to be recognized.

I also have this other card:
```
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
```
that works with the nvidia legacy driver.

anyone knows why this onboard card isnt being recognized? It used to work when I didn't have the TNT2 card.
I think it is enabled at bios, but I'll post the bios configuration next time I reboot.

thanks

---

### Post by tonyhawz on 2007-11-29
my bios configuration under 'PCI / plug and Play setup' is;
```
Share Memory Size               64MB
Primary Graphics Adapter        AGP
Allocate IRQ to PCI VGA         Yes
PCI IDE Busmaster               Enabled
```

I also wanted to know in which log should I take a look to see if anything is going wrong.

thanks

---

### Post by tonyhawz on 2007-11-29
well I just found that it isn't possible.

> Yes, when installing an AGP card the onboard will automatically disable. No way around that. I would think, tho, that adding a PCI video card would still let you use the onboard

I just read it from [http://forums.viaarena.com/messageview.aspx?catid=31&threadid=79964&enterthread=y]("http://forums.viaarena.com/messageview.aspx?catid=31&threadid=79964&enterthread=y")

---

