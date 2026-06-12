---
title: "lircd detects incorrect remote"
date: 2011-04-19
forum: Mythbuntu
---

### Post by Kr0nZ on 2011-04-19
Hi, My mce remote had been working fine with lircd for the past 3 weeks or so
when I would run irw i would get lines like :
```
000000037ff07bd9 00 Guide mceusb
000000037ff07bde 01 Right mceusb
```
using mceusb my remote worked perfectly

But when I came home one day the IR receiver light was on constantly and would respond to any input from my remote,
to get any kind of response from it I had to kill lircd unplug the receiver, then replug it and restart LIRCD.

After doing that my remote would only half work, and running irw again instead of getting mceusb I get lines like:
```
000000037ff0ebe1 00 Up vista_mce
000000037ff0ebe1 00 Up_UP vista_mce
000000037ff06bde 00 Right vista_mce
000000037ff06bde 00 Right_UP vista_mce
```
 

So for some reason my remote is being detected as vista_mce, instead of mceusb like it was before when working fine.

Is there any way to force lircd to use mceusb instead of vista_mce?
or is there any other way to fix this?
Thanks for any help

---

### Post by azmyth on 2011-04-20
I'd look in your /etc/lirc/hardware.conf file to see if something changed under REMOTE_MODULES.

---

### Post by Kr0nZ on 2011-04-21
my hardware.conf looks fine, when i was initially setting up my remote i had to add lirc_ to mceusb on the REMOTE_MODULES line to get it to work.

But i had just completed a reinstall of mythbuntu(i needed to reorganize my partition's anyway, plus the kernel crashed and couldnt boot anymore), but this time i didnt need to add lirc_ to mceusb on the REMOTE_MODULES line, but the remote still shows as vista_mce in irw, it behaves REALLY slow and the OK button doesnt work.

Yeh so even a OS reinstall couldn't fix the remote, im not sure what else to do

---

