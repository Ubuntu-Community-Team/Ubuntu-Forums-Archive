---
title: "[SOLVED] Sound works for some games, but nothing else"
date: 2008-07-13
forum: Multimedia Software
---

### Post by stwert on 2008-07-13
Hi, I'm new to Linux, and am having lots of problems with my sound. I tried the comprehensive sound guide when I wasn't getting any sound, and I'm not sure how much it helped, because I still don't get anything from CDs, movie files, internet, sound effects, anything. However, I was playing a couple of games to try them out and I noticed that in Neverputt, and SuperTuxKart, there were sound effects and music. Obviously the sound CAN work, and it's not just muted, so what's up?
My sound card is a Creative Labs SB Audigy LS
Thanks for any help/ideas , this basically the only reason I'm still using windows for anything right now. 

BTW, I don't get any sound from nibbles, with SFX enabled, so it's not just/all games that work.

---

### Post by stwert on 2008-07-14
Just to give some more information as I'm trying different things; it seems as though Ubuntu is still trying to use my on-board sound card, because the hardware testing application detected a sound card: V8237, which isn't my CreativeLabs SB Audigy.

aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

(sorry, don't know how to put the code in the box/font thing)

Anyway, hopefully that will give someone an idea of what the problem is. I'm willing to get inside the computer and move around jumpers etc, if necessary, but I'm hoping the solution is more elementary :)
Thanks

---

### Post by prshah on 2008-07-14
> **stwert said:**
> 
it seems as though Ubuntu is still trying to use my on-board sound card, because the hardware testing application detected a sound card: V8237, which isn't my CreativeLabs SB Audigy.

aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]



You can disable onboard sound from the CMOS setup (BIOS). (Press DEL or F2 during startup, usually) Since you know about jumpers, I assume you can take it from here; otherwise, post back for more information.

btw, jumpers are now stone-age :) Now it's aaaalllll PnP

Yabba-dabba-doo!

EDIT: Just realized that a simpler thing to do would be to tell ubuntu to use only the Creative card in System-Preferences-Sound; but then again, I'm anything but simple.

btw, if you wrap anything with ```
 tags, it will give you the text/font thingy eg: [code][code ]testing[/code ]
``` Please remove the spaces I've put in, or else it wont work...

---

### Post by stwert on 2008-07-15
Awesome!!!
I went into the BIOS and disabled the on-board sound chip. And now I have sound!! I actually don't really know much about BIOS and jumpers and stuff, but I guess it all worked out, it was pretty intuitive. 
Thanks so much for the advice. I'm postponing my next Windows visit indefinitely.

```
 sudo wget test 
```

(just testing the code tags)

---

### Post by prshah on 2008-07-16
> **stwert said:**
> I'm postponing my next Windows visit indefinitely.



```


                       ----------
                      /          \
                     /    REST    \
                    /      IN      \
                   /     PEACE      \
                  /                  \
                  |     windows      |
                  |                  |
                  |  lost out to yet |
                  | another satisfied|
                  |  user: stwert    |
                  |                  |
                  |    ???? - 2008   |
                 *|     *  *  *      | *
        _________)/\\_//(\/(/\)/\//\/|_)_______


```

You should mark this thread as solved; click on "Thread Tools" near the top right hand side of this page, then choose "Mark as solved" (or words to that effect.)

---

