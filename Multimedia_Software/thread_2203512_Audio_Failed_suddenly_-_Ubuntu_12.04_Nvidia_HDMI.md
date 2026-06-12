---
title: "Audio Failed suddenly - Ubuntu 12.04 Nvidia HDMI"
date: 2014-02-03
forum: Multimedia Software
---

### Post by EternalStudent on 2014-02-03
I am pretty confused at the moment.  Pretty new to linux, especially this aspect of it.  I've used Mythbuntu for several years now.  Recently, I upgraded to 12.04 and a HDMI capable graphics card.  I successfully ran audio over HDMI after doing some reading and following steps on this link: [https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#).   

Yesterday, while watching a mpeg video, audio went out.

Started to looking around and it appeared that the sound out of one of the nvidia devices had failed (the card has 2: 1,3 and 1,7)  switched to 1,7 but that did not fix anything.  then after a reboot stuff got worse.

aplay -l results in this:
```
~$ aplay -laplay: device_list:252: no soundcards found...

```

alsamixer this:
```
~$ aplay -laplay: device_list:252: no soundcards found...



```

not convinced this was a good idea, but it seemed so at the time:
```
[FONT=Ubuntu Mono]sudo apt-get remove --purge alsa-utils
[/FONT][FONT=Ubuntu Mono]sudo apt-get install alsa-utils[/FONT]
```

How do I get myself out of this hole?

Thanks!

---

### Post by EternalStudent on 2014-02-03
Oh, also, I booted from a live usb and aplay - l lists devices.

---

