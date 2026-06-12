---
title: "Finally Got my Tuner working...BUT"
date: 2006-05-26
forum: Multimedia &amp; Video
---

### Post by hellmet on 2006-05-26
After lotsa search..I found out that my actual card and tuner values..
Now I can see that the applications have identified the tuner as
FLYVIDEO2000...

In KDETV I can hear the buzzz sound and can also see that there is no channel
...u see all those grains rite..
But I am not able to grab onto any channel...
I have tried US cable and EUrope-WEst...
But no channels to be found!!!:( 
I was so excited I finally set up my card..but ..

Can somebody tell me where I am going wrong??
Or is it possible that even after getting the Tuner to work,
I may have set the wrong tuner or card value???
I live in India...
Somebody helpp!!!

---

### Post by hellmet on 2006-05-26
> DMESG gives
this

[4294715.389000] saa7130 [0 ]: found at 0000:06:00.0, rev: 1, irq: 21, latency: 32 , mmio : 0xff7ffc00
[4294715.389000] saa7130 [0] : subsystem: 18d0 :2100, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[4294715.389000] saa7130 [0] : board init: gpio is 38500
[4294715.389000] saa7130[ 0]: there are different flyvideo cards with different t uners
[4294715.389000] saa7130[0] : out there, you might have to use the tuner=<nr> ins mod
[4294715.389000] saa7130 [0] : option to override the default value.
[4294715.390000] saa7130 [0] : registered input device for IR
[4294715.501000] saa7130 [0] : i2c eeprom 00: d0 18 00 21 10 28 ff ff ff ff ff ff ff ff ff ff
[4294715.501000] saa7130 [0] : i2c eeprom 10:  ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294715.501000] saa7130 [0] : i2c eeprom 20 : ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294715.501000] saa7130 [0 ]: i2c eeprom 30 : ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294715.513000] tuner 0-0061: chip found @ 0xc2 (saa7130[0])
[4294715.513000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compati bles))
[4294715.533000] saa7130  [0] : registered device video0 [v4l2]
[4294715.535000] saa7130  [0] : registered device vbi0
[4294715.537000] saa7130  [0] : registered device radio0

and a wierd msg

[4294767.206000] tuner 0-0061: TV freq (32.06) out of range (44-958)



Please tell me if u can understand anything

---

### Post by leo_m on 2006-07-04
um, could it be that you are using a wrong TV-standard setting (e.g., using Europe when you are in India) ?

Try using the proper TV-standard (e.g., in TV-Time it is available on the menu-options which you can access by right clicking inside the TV-Time display window).

Once you have corrected your TV-standard setting, then you should scan for channels...

---

### Post by hellmet on 2006-07-07
sorry for not telling..
I solved the problem..
I also posted the solution in a 
separate thread.
Thanks..

---

