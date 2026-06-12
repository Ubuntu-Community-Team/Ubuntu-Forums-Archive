---
title: "ATI HD 2600 laptop with external monitor"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by mlak on 2008-03-09
Hi,
Please excuse the inciomming wall of text.

Im using ubuntu gusty on a toshiba p200 laptop, after weeks of tweaking i managed to get everything working, most of the problems were with the headphone jack and the ATI mobility radeon HD 2600,

after following 100's of guides and posts i managed to get compize, 3d windows and everything working properly (using fglrx).

now i got a new 22" monitor @ home, i connect it to the VGA port on the labtop and so far i have not managed to get them both to work. if i try to use big desktop, the 22" become the primary monitor, and the size of the 1280x800 laptop screen is reduced to 640x480. i have yet to manage to turn the 22" external monitor into the secandary monitor.

i also tried the dual-head option of the aticonfig utility, i managed to get it working only once at the correct resolutions for both screens (22" on 1680x1050 and 15" on 1280x800). and then runied it by trying to get compize to work with dual-head, which i never managed to do as well. also in this mode dragging a window on the 22" is extreamly slow ( though movies play normally)

anyone that has got a simillar setup running please help.

and im sorry i didnt include any xorg.conf file its just that i got about 500 of them now and none really work.....

---

### Post by mlak on 2008-03-09
Ok i give up. i wasted another day on this. every time i get one thing working another thing breaks, i cant belive there arent any gusty users with a ati HD 2600 labtop that have run into this before.

anyway now im just trying to get clone mode to work with diffrent resolutions.
i know it defies the idea of clone but aticonfig help states:

```
-dtop, --desktop-setup=STRING
        Change the desktop setup for multiple display adapters.
        STRING can be one of:
            single              1 screen, second dark
            mirror              2 screens - same content, identical
                                refresh rate/resolution
                                Note: This option is NOT supported with Avivo
[B]            clone               2 screens - same content, allows for
                                different refresh rates/resolutions
[/B]
```

so if anyone has this working please state how,
Thanks.
-Rob.

---

