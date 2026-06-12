---
title: "strange behavior with streamzap remote"
date: 2014-06-20
forum: Mythbuntu
---

### Post by ahood on 2014-06-20
Hello,

Struggling to get Streamzap remote working properly with mythbuntu (12.04) with mythfrontend fixes/0.27 (v0.27.1-14-g2720f45).

I successfully disabled xinput recognizing the remote as a keyboard.

I successfully installed lirc and can verify button mapping with irw.

After launching myth frontend, I can use buttons to scroll up and down of main menu, and use OK button to move to a submenu.

Then, the strange behavior happens. I cannot scroll the Watch Recordings list of TV programs, nor the list of Watch Videos. When these lists appear, the red light on the IR receiver blinks constantly for listings that are the second submenu.

The red IR receiver light does not blink constantly for the main menu, nor the first submenu. it seems only the second submenu has the problem.

Will appreciate any pointers to a solution for this Streamzap remote. Suggestions for an alternative remote is also welcomed.

With kind regards. 

DrH

---

### Post by ahood on 2014-06-22
After hours of searching the Internet and trying and failing all of the possible solutions, the Streamzap remote will be returned. It just doesn't work reliably with Mythbuntu 12.04/mythtv 0.27 and lirc, inputlirc, or natively. It is definitely not an OTB device. The closest I came is with lirc and disabling native support, but experienced the problem described above, which makes the remote unusable.

---

