---
title: "Mackie Spike USB card problems under Feisty"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by tictactatic on 2007-05-08
Hi,

I bought a Mackie Spike USB card upon friend's recommendation that it just worked (TM) for playback under Edgy. 

I plugged it into my Feisty machine only to find out that it didn't just work, though $ cat /proc/asound/cards gave:

 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 0 with AD1888 at 0xfe800000, irq 19
 1 [XD2            ]: USB-Audio - Mackie XD-2
                      Mackie Designs Mackie XD-2 at usb-0000:00:13.0-1, full speed

If i set up hw:1,0 as the playback device in Amarok it wouldn't work. Only after it occurred to me to try plughw:1,0 Amarok started playing fine.

So so far so good, but I am having trouble getting other applications, namely alsamixer (gives me "no mixer elems found" when i run alsamixer -c 1) or kmix (only shows the ATI IXP)... Not to mention that Audacity crashes when i select the hw:1,0 option from its dropdown menu as a playback or recording device).

Any ideas how I could fix at least some of these issues?

---

