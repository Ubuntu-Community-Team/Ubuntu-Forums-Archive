---
title: "S/PDIF with a CM8738"
date: 2009-12-28
forum: Multimedia Software
---

### Post by aehirst on 2009-12-28
I have 2 sound cards, an internal card which I use for my stereo out. I also have a digital sound card ( CM8738 ) with an optical out.

However when I try to use the digital out I get silence. I have set all volume levels and set the profile to digital but nothing seems 
to work. I'm using 9.10.

Anyone have any ideas?

Thanks

---

### Post by Alpha1Dash1 on 2010-01-05
Just been through this process myself [my old Audigy2 died & I replaced it with a Trust SC-5250, which is seen as a CM8738]. 

All my problems were solved using the alsamixer utility. The steps I went though were:

1) make sure alsamixer is installed using synaptic.
2) open terminal and run alsamixer. Scroll right (cursor keys) to the column called "IEC958 O" [ = IEC958 Output].
3) If the column shows a small box with "MM" in it, digital output is disabled. Use "m" to toggle it on and it should now show a high-lighted green "00".
4) If you want analogue output as well (as I do for my mic/headset), then scroll left to the "IEC958 In Monitor" and toggle it on.
5) exit alsamixer using <Esc>. [not actually sure if this is needed to save the settings, but its what I did!].

Hope this works as well for you as it did for me!

---

### Post by longfins on 2010-03-07
Thanks George, that fixed my problem, on Ubuntu 9.10

---

### Post by nickdngr on 2010-06-01
George, thank you so much! I spent hours trying to figure out why this wasn't working and it never dawned on me that there were alsa options unchecked! Thanks again.

---

### Post by uOpt on 2010-06-01
Are you able to use the S/PDIF input on that card?

I have difficulties with mine. Sometimes it works right after a reboot for a while, but pretty quickly it gets me into read errors and stays that way. Most of the time it doesn't work after reboot in the first place.

---

### Post by Alpha1Dash1 on 2010-06-01
longfins & nickdngr: Glad to hear the fix worked for you two - there is probably some super-smooth way of doing it without using alsamixer, but I have no idea what it is! 

uOpt: sorry, I don't know - I have no s/pdif ouput devices to connect.

---

### Post by ferdije5 on 2012-05-21
fantastic thanks can't believe solved 2 problems in less then one hour spotify and this one I tried windows 8 to but ubuntu is much better with multiple desktops get crazy in eight haha
registered at once for the next issue which  might occur

---

