---
title: "Karmic: nvidia-glx-71"
date: 2009-11-04
forum: Multimedia Software
---

### Post by nisix on 2009-11-04
Will karmic have nvidia-glx-71 available in its repos? I need it for my geforce2 gts card as the other legacy driver (nvidia-glx-96) doesn't support it.

---

### Post by RFXCasey on 2010-01-18
I'd like to know the same thing because I am having a heck of a time getting my Nvidia GTS to work well under Karmic. I mean I have video but it doesn't say it is using any proprietary driver for the card and I think my video performance should be a whole lot better then it is right now.

---

### Post by _6i on 2010-04-10
same here:
i have a machine which has a GeForce2 Ti graphics card and it is no more supported from driver versions 96 and up (which are supported by karmic)
because i suspect, lucid won't have it either and i didn't want to revert to jaunty (which had the package), i tried to use the 71 driver from the nvidia page: i installed it, but i couldn't set i up (i think) or check whether the system using it (instead of the default open source driver)
i couldn't make the utility provided by nvidia to set up x.org (no 'configure' script, 'make' and 'make install' ran with errors, but installed the utility nevertheless, which generated a /etc/X11/XF86Config file without any prompt or choices, but X couldn't use it when i started it afterwards..)
also, the [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) site didn't have instructions for karmic

 had anyone any luck with the official nvidia 71 driver on karmic?

---

