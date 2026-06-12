---
title: "I can't get any sound from my audio interface"
date: 2010-11-01
forum: Multimedia Software
---

### Post by BcRich on 2010-11-01
Hi 
i recently got a new audio interface, which is working perfectly on ubuntu 10.04 i just plugged it in and it worked without any tinkering! the interface is a lexicon omega which is fully supported under alsa. The problem is that for some reason it's not working on ubuntu 9.04 (which is where were most of my work currently is so occasionally i still have to use 9.04 as i don't have all of the same software installed on 10.04).
jack seems to detect it properly in both 9.04 and 10.04 as it is listed in "interfaces". But it does not show up in "Volume Control Alsa Mixer" so I cannot select it from the drop down list.
So currently I have no sound :(
does any one have any suggestions as to why this might be happening?
oh and i'm still a newbie (just in case you weren't able to decipher that from my primitive ubuntu-speak above :) )
here's the output of cat /proc/asound/cards
```

 0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0x9c00, irq 16
 1 [U0x46d0x8b2    ]: USB-Audio - USB Device 0x46d:0x8b2
                      USB Device 0x46d:0x8b2 at usb-0000:00:10.0-2, full speed
 2 [Omega          ]: USB-Audio - Lexicon Omega
                      Lexicon Lexicon Omega at usb-0000:00:10.1-1, full speed

```
please let me know if there is any further information i need to submit?
thanks for your help!

---

### Post by BcRich on 2010-11-01
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

i seem to recall blacklisting my onboard soundcard a long time ago I don't quite know what that means or why i had to do it, but i seem to recall that it got ubuntu to stop using my onboard sound and defualt to my audigy soundcard. 
does this have something to do with the reason ubuntu 9.04 is unable to use my new sound interface?

---

### Post by BcRich on 2010-11-20
it's working now, dunno why. it just is. :)

---

