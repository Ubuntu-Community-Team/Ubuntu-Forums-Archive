---
title: "No sound on headphones"
date: 2015-01-26
forum: Multimedia Software
---

### Post by flitzpiepe on 2015-01-26
Hey there!

I've installed Ubuntu 14.04 on a Lenovo ThinkPad E555 AMD A8-7100.
It runs fine except that my headphones and other external speakers don't work.
If i plug a device in, there's absolutely no effect. Internal speakers work fine.
Asamixer shows no bar for headphones. Muting/unmuting has no effect. 

lspci -nnk | grep -i audio -A2 :
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:1308]
    Subsystem: Lenovo Device [17aa:5110]
    Kernel driver in use: snd_hda_intel
--
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
    Subsystem: Lenovo Device [17aa:5110]
    Kernel driver in use: snd_hda_intel

cat /proc/asound/cards:
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0b40000 irq 89
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0b44000 irq 16
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw unknown


Would be really grateful for any advice as i have no idea how to fix this on my own...Cheers!

---

### Post by Stueck on 2015-03-18
I described my workaround here and I hope this works out for you:  [http://askubuntu.com/questions/585709/headphones-not-recogised/598463#598463](http://askubuntu.com/questions/585709/headphones-not-recogised/598463#598463)

---

