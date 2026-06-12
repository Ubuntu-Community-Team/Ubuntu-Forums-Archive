---
title: "VIA 8235 Sound is lagging after 200 Mo of Dapper's update"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by nicobbg on 2006-07-20
After a daily update of Dapper and a reboot, my sound is lagging. :-k  
At the GDM, the drum sound is looping. The loggin step is very slow but a top cmd does not show any process loading the CPU or Mem.
When I play an .mp3 file with BMP it's lagging also.

I can't find any help on the french forum (you didn't notice my bad english? :cool: ). I already tried to reinstall Dapper, it works before I update any packages and after I update all my packages and reboot the same problem apears again. ](*,) 

My motherboard is a DFI AD77 Infinity
[http://eu.dfi.com.tw/Product/product_search_result_us.jsp?PRODUCT_ID0B=1010&SITE=UK](http://eu.dfi.com.tw/Product/product_search_result_us.jsp?PRODUCT_ID0B=1010&SITE=UK)

Is anyone able to help me?

aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: V8235 [VIA 8235], périphérique 0 : VIA 8235 [VIA 8235]
  Sous-périphériques: 4/4
  Sous-périphérique: #0: subdevice #0
  Sous-périphérique: #1: subdevice #1
  Sous-périphérique: #2: subdevice #2
  Sous-périphérique: #3: subdevice #3
carte  0: V8235 [VIA 8235], périphérique 1 : VIA 8235 [VIA 8235]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

---

### Post by nicobbg on 2006-07-21
Up, Up,
Bouuuuu, please help :'(

---

### Post by nicobbg on 2006-07-21
I've finally found a solution on the french forum.
It is the 2.6.15-26 kernel that seems to be bugged. I downgraded to 2.6.15-25 and it works again.

---

