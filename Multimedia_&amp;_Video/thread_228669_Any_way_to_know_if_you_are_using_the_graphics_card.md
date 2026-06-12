---
title: "Any way to know if you are using the graphics card own memory?"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by shdgrao on 2006-08-03
Hi. I have an ati mobibility radeon 9600 card in my laptop and Ubuntu 6.06 installed. I was running all the programs using the default driver for this card in Ubuntu, without 3d acceleration. I supposse that in this conditions I wasn't using the graphics card memory (I don't know). I would like to know any method to find this out (If I am using the graphics card memory or not), because now I have installed the ati drivers for the card and I can see no differences in the memory usage.

Thanks.

---

### Post by kaffelars on 2006-08-04
I have a Mobility Radeon 9700. 
I have installed the ATI drivers and the restricted modules-package, and changed the driver in the xorg.conf to "fglrx". 
This was all I had to do get 3D, and I'm pretty sure the card's own memory is used :) (However, I don't know how to check this..)

---

### Post by tseliot on 2006-08-04
The fact of using your system memory or your graphic card memory depends on the BIOS and not on the drivers.

---

