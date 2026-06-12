---
title: "mega huge video card problem"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by superjeff on 2007-08-08
first off, i'd like to apologize if i didn't search hard enough. hope i don't ruin anyones day.

i'm really new to ubuntu. like...border line dumbass new. on my first boot into ubuntu, i was given some error about my nvidia drivers being restricted. i tried to check the box in the restricted drivers program deal, and it said it was downloading, but then it asked me for a ubuntu cd. i cancelled out of it. i then did some searching around, and ended up doing the following:

sudo apt-get install nvidia-glx-new

it ran through the some processes, everything looked good

glxgears

i saw three gears turning, smiled, and rebooted like i was told to. ubuntu didn't boot. it took me to a screen that looked like a BIOS, and, i'm sorry, i can't remember exactly the error, but something about my xsomething or other (i know, i'm butchering all this)...basically it was a huge graphics card error, because it had to take me to screens that look like BIOS because they're completely graphics free. it asked me if i wanted to view some stuff to check for errors, and i did. i didnt know what to change, so i didnt change anything and it booted to a black screen where i could just type code. basically command prompt. i typed some stuff out of anger, and finally tried sudo reboot or something like that, and rebooted into the vista i'm in now. i'm trying to avoid having to type out all that stuff it showed me, but if i have to, i guess i will. hopefully you guys know a simpler fix. i'm less than 24 hours into my linux journey, so please bare with me. thanks for your input.

---

### Post by superjeff on 2007-08-08
ok, i've got more useful info. the error goes something like this:

Error: API mismatch: the NVIDIA kernel module has version 1.0-9755, but this x module has the version 1.0-9631. Please make sure that the kernel module and all  NVIDIA driver components have the same version.

then it tells me to make sure i have a supported gpu (mine's geforce go 7200) and that the device files have been created properly. this is all an xserver crash i've found out, and i have no idea what to do from here. im pretty sure i installed the wrong drivers or something and i need to figure out how to go back to the way it was before i tried to use those restricted nvidia drivers. i would really appreciate any input. thanks.

---

