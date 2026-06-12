---
title: "Alsamixer and headphones problem"
date: 2019-11-20
forum: Multimedia Software
---

### Post by ollylove on 2019-11-20
Hi beautiful people!!

So, I freshly installed kubuntu 18.04 LTS (on my MSI GE75 Raider 9SF-1067UK) and everything works fine, apart from the audio with headphones.. when I plug in my headphones, alsamixer mutes the speakers and unmutes the headphones (which is correct), but this way the volume from the headphones is very low and even if I raise Master volume to 100%, is stays fixed low.. BUT, if in the terminal I manually unmute the speakers and raise the speakers volume, it works, the volume from the headphones raises accordingly, I can set it to 100% and control Master volume with arrow keys and all goes smoothly.. just, alsamixer doesn't remember these settings and if I unplug the headphones and plug them in again, the problem starts over, I have to manually unmute and increase the Speakers volume again..

Note that even if I unmute the speakers, they don't emit any sound, it still comes from the headphones!!

Doesn't this sound a bit wrong??.. I should be able to control the *Master* volume for both speakers and headphones, right??

Also, Auto-mute mode is Disabled.. does that mean that when I plug in the headphones alsamixer should NOT switch off volumes??

Anyway, how do I solve this problem??.. I thought I could create a custom shortcut for increasing/decreasing the Speakers volume and use them when I plug in my headphones.. I already tried to follow the solution provided in the link below - by setting as command 
```
amixer -D pulse sset Speaker 5%+
``` 
but it doesn't work: [https://askubuntu.com/questions/181341/how-do-i-set-a-custom-keyboard-shortcut-to-control-volume](https://askubuntu.com/questions/181341/how-do-i-set-a-custom-keyboard-shortcut-to-control-volume)

Any other solutions??
Thanks in advance!!
Olly

---

### Post by ollylove on 2019-11-21
Hello??

---

### Post by richard1937 on 2020-08-16
This is still a problem  with MSI's GE75,   mine doesn't work either.   I also tried MINT20 and that doesn't work either. All OK with Windows, so HW is good.   In my case the headphones work but the internal speakers do NOT work.  Also in Alsamixer there is no slide volume for the speakers and headset.   JUST the Master Volume and other Audio "points"  
Help,  My time to return this is running out at this rate.

---

