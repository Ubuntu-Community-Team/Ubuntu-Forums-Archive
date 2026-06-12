---
title: "No pcm digital audio problem"
date: 2009-04-16
forum: Multimedia Software
---

### Post by Turex on 2009-04-16
Hi

Os: ubuntu 9.04 ( upgraded from 8.10)
soundcard: ADI1988a ( Asus m2r32-mvp integrated)
Connection: Coax spdif


I have this crazy problem which appeared suddenly after reboot. My analog audio out works perfectly and spdif out ac3/DTS passtrough also works fine atleast with xbmc. But when i try to listen music or something, which uses pcm digital out, it just won't work. 

My volume controls are ok. Most strange thing is that it worked perfectly until i rebooted one day. I don't now what could have changed, apart from installing and configuring mythTV. Could mythTV screw up pcm digital out ?

Please i'm out of options and i don't want to reinstall. ( BTW. i tried ubuntu 8.10 live CD and it worked !! ) What should i do ?

aplay -l output:
( in finnish sorry )
```
**** Luettelo PLAYBACK laitteista ****
kortti 0: SB [HDA ATI SB], laite 0: AD198x Analog [AD198x Analog]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: SB [HDA ATI SB], laite 1: AD198x Digital [AD198x Digital]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0

```

Edit: Upgraded to ubuntu 9.04 to see if my problems magically disappear ( they didn't)

---

### Post by Turex on 2009-04-16
bump :KS

---

