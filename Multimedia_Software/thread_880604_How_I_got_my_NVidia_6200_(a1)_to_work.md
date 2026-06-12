---
title: "How I got my NVidia 6200 (a1) to work"
date: 2008-08-05
forum: Multimedia Software
---

### Post by jds340 on 2008-08-05
Seeing as the "Post how you got your NVidia card to work" thread is closed I thought I'd post a new thread in case someone else has my problems.

I have a GeForce 6200 (a1) card. The result of lspci -n | grep 0300 is 01:00.0 0300: 10de:0221 (rev a1)

Working with 8.04, I installed the proprietary drivers all OK using the built in installation routines (no need for Envy). Everything was working, but I was stuck with a low screen res and simply couldn't get the thing to find the higher screen resolutions available. Compiz and stuff worked but with ultra low res why bother.

Reading "Hacking Ubuntu", in desperation I found the comment "During installation Ubuntu detects the graphics ..... The detection is done using the ddcprobe and xresprobe commands. So I tried them out, and.... They weren't there. 

So I then did "sudo apt-get install ddcprobe xresprobe" which fixed the problem. After a reboot the system could see all the higher resolutions on the card. Why these seemingly essential tools weren't available after a clean install is a mystery however.

Otherwise I'm finding Ubuntu really cool and will be switching other machines over from Windows

John Small

---

