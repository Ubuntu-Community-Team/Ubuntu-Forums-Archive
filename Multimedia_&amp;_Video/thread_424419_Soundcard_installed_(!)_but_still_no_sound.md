---
title: "Soundcard installed (!) but still no sound"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by zjameria on 2007-04-26
Relatively newbie here. I upgraded from Edgy to Feisty. Sound didnt work before and its not working now either. I have Gateway M210 Laptop with Integrated ADI 1981B sound card. In XP, this is recognized as Soundmax card and works fine. So hardware is not broken for sure. 

It seems like the sound card is recognized in Ubuntu and installed as well, but no sound comes out of it. I checked and made sure that nothing is muted. I also tried alsamixer from terminal and checked that nothing is muted.  I finally fixed wireless, but cant get around this sound issue. Any help would be greatly appreciated. 

This is what I get after aplay -l in terminal. (Does this mean the sound card is installed? because I can change the volume and everything. I can even control volume from the knob on the laptop)

```

zenith@Bubby-Gubby:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
zenith@Bubby-Gubby:~$ 
```

Thanks.

---

### Post by samuliri on 2007-04-27
check this:
[http://ubuntuforums.org/showthread.php?t=418360](http://ubuntuforums.org/showthread.php?t=418360)

---

### Post by zjameria on 2007-04-27
I just tried that as well and everything went smoothly without errors. But still, there is no sound.

Thanks for your help. 

Any suggestions are welcome!
This is one thing thats frustrating me.

---

