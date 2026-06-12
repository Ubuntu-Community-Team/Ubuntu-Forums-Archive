---
title: "Capturing output of arecord in a C program"
date: 2012-06-25
forum: Multimedia Software
---

### Post by amarshat on 2012-06-25
I am trying to popen the arecord command in a c program to capture the Max Peaks output, however its not working as expected.

If I directly execute this command, 

arecord -Dpulse_monitor -c2 -fS32_LE /dev/null -vvv 2>/dev/null | grep Max

I get out put like, 

Max peak (2000 samples): 0x00000000 #                    0%
Max peak (2000 samples): 0x00000000 #                    0%
Max peak (2000 samples): 0x00000000 #                    0%
Max peak (2000 samples): 0x00000000 #                    0%
Max peak (2000 samples): 0x00000000 #                    0%
Max peak (2000 samples): 0x00000000 #                    0%


However, when I try to read the output in a c program, like,


FILE* proc;
    proc = popen("arecord -Dpulse_monitor -c2 -fS32_LE /dev/null -vvv /dev/null | grep Max", "r");

I dont get the expected output when I do a fgets. Same is the case with ruby, I am not getting the continuous  of IO.popen(cmd, "r"). 

Can any one explain why this is happening and a work around to be able to grab Max Peaks for a sound device. ?

---

