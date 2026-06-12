---
title: "M-Audio delta 44"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by grizlord on 2006-06-25
I recently purchased a delta 44 sound card and I'm having trouble getting it configured in Dapper. I've read about envy24control in other threads but can't find an easy way to make it work! I'm pretty new to ubuntu and am hoping someone will show me how to get everything set up via comand line. would much appriciate any help you could give me.
Thanks

---

### Post by zettberlin on 2006-06-25
What is the Status right now? Is the card working at all (it should absolutely ...) what happens, if you start envy24control? And Alsamixer?

Have you disabeled the onboardsoundchip of your motherboard?

The card should work right away. I know several people, that run it with ubuntu and could not tell how to set it up because they did not need to touch anything to make it run ;-)

---

### Post by grizlord on 2006-06-26
I have'nt disabled the sound chip on my mother board, when I run alsamixer the only card it lists is the other card (Intel 82801DB-ICH4) with Realtek ALC202 rev 0 chip, not the delta? Is envy24control built in to Dapper or do I have to add repositories to get it? ;)

---

### Post by zettberlin on 2006-06-26
[QUOTE=grizlord]I have'nt disabled the sound chip[/QUOTE]

I made several experiments with lots of headaches and no success with having 2 Audiocards enabled - I absolutely recommend to disable the onboardchip (and the gameport). 

[QUOTE=grizlord]
  Is envy24control built in to Dapper or do I have to add repositories to get it? ;)[/QUOTE]

it is in universe named alsa-tools-gui (hdspconf and some others are installed also - we only need envy24 anyway ...)

---

### Post by grizlord on 2006-06-27
To disable my unwanted sound card should I remove it from my box altogether, or is there a comand line script to disable one and enable the other?

---

### Post by zettberlin on 2006-06-27
this is not to be done at OS-level. To disable conflicting or unwanted hardware you have to enter your computers BIOS right before GRUB starts. Usually you have to push DEL or ESC after you switched your box on.

BIOS-Setting is not as complicated as it looks - use Google to find a plethora of HOWTOES ;-)

---

### Post by blackgibson on 2006-07-08
> this is not to be done at OS-level. To disable conflicting or unwanted hardware you have to enter your computers BIOS right before GRUB starts. Usually you have to push DEL or ESC after you switched your box on.


mmm.. Wouldn't adding the offending driver/module to /etc/modprobe.d/blacklist also work? Especally if you are using a dual boot as disabling in BIOS would render the hardware unavailable to other OSes that it may be behaving in, Just a thought

---

### Post by zettberlin on 2006-07-08
/etc/modprobe.d/blacklist should do as well yet i tend to be quite radical regarding such matters - if one invests into a delta-card he/she is probably into hi-class/semipro audio - so an onboardchip is of little use and disabeling solves the problem fast and secure ;-)

---

### Post by hanzomon4 on 2006-07-09
You could try going to Preferences>sound and change the defualt sound card.
Might work.

---

### Post by hanzomon4 on 2006-07-09
This [link]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=cd") Should help with all of your soundcard problems

---

