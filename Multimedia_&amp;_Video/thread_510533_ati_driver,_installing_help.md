---
title: "ati driver, installing help"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by richard6865 on 2007-07-26
hello all i was wondering if anyone can help me out as i am trying to install an ati driver that i got off there website. my graphics card is "ati mobility redeon 9000 igp" 

now when i try to install it in the terminal it looks like it does it's stuff untill i get and error message saying

"./ati-installer.sh: 165: syntax error: bad substitution 
removing temporary directory:fglrx-install"

this thing has been pecking my head for days i have search the net far and wide and still now answer so yeah if you can help, HELP!

thanks richard

p.s. if you want a screen shot let me know

---

### Post by zieklecknerizer on 2007-09-15
yea i have had the exact same issue and i have no idea i have the ati radion 2500 series i need to know how to fix it

---

### Post by w4ett on 2007-09-16
> **richard6865 said:**
> hello all i was wondering if anyone can help me out as i am trying to install an ati driver that i got off there website. my graphics card is "ati mobility redeon 9000 igp" 

now when i try to install it in the terminal it looks like it does it's stuff untill i get and error message saying

"./ati-installer.sh: 165: syntax error: bad substitution 
removing temporary directory:fglrx-install"

this thing has been pecking my head for days i have search the net far and wide and still now answer so yeah if you can help, HELP!

thanks richard

p.s. if you want a screen shot let me know

The chipset you have is not compatible with the fglrx drivers from AMD/ATI. the restricted driver only supports the 9500 chipset/cards and above. see:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Your card is supported by the xorg-driver-ati, which is the open source driver included with Feisty.

---

