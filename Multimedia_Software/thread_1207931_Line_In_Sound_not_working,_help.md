---
title: "Line In Sound not working, help?"
date: 2009-07-08
forum: Multimedia Software
---

### Post by Turtleman on 2009-07-08
Hey. I need line in sound in my computer so I can hear my xbox 360 sound through my computer sound system, but my Line In is not working. Does anybody know how to make it work? I read in the sound troubleshooting documentation that my sound card needed to configure something to make line in work but I didn't understand at all what I was supposed to do. This is my sound card:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Thanks for your time

---

### Post by Turtleman on 2009-07-08
bump

---

### Post by adasadas on 2009-07-08
> **Turtleman said:**
> Hey. I need line in sound in my computer so I can hear my xbox 360 sound through my computer sound system, but my Line In is not working. Does anybody know how to make it work? I read in the sound troubleshooting documentation that my sound card needed to configure something to make line in work but I didn't understand at all what I was supposed to do. This is my sound card:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Thanks for your time

Same problem here :( Help us please :')

---

### Post by Turtleman on 2009-07-08
Here is a tip man, I stil haven't got both line in and mic to work at the same time, but I found out if I connect my xbox sound cable in the mic (the pink one) it works like line in. So if you dont need mic and line in at the same time, that will help you. As for me, I want both, so I am still trying to figure it out. 

Note: Don't forget to check on volume control and put the mic sound up.

---

### Post by Turtleman on 2009-07-09
Bump

---

### Post by Turtleman on 2009-07-09
Bump

---

### Post by malrost on 2009-07-09
Can you please post a screenshot of the results of the following command:

```
alsamixer -V all
```

---

### Post by Turtleman on 2009-07-09
Here it is:

---

### Post by malrost on 2009-07-09
I think you might have the wrong sound module loaded for your card.

This page might help. It's Arch Linux though, so the package manager is different from Ubuntu -- avoid all the "pacman" commands. Instead use Synaptic Package Manager and check that the following packages are installed (if not, install them). Search for "alsa" and you'll find:

libasound2
lib32asound2
alsa-utils
alsa-oss

Basically you'll then use these tools to first check that the proper sound modules are currently loaded in the kernel, and if not you will load them. You will have to unload & reload your sound (two commands) when you change sound modules for them to actually work:

```
/etc/rc.d/alsa restart

```

(Rebooting will serve the same purpose, but takes a lot longer.)

You will start by checking the output of this,

```
lspci
```

this,

```
lsmod|grep '^snd' | column -t
```

and this,

```
ls -l /sys/module/snd/holders
```

---

### Post by Turtleman on 2009-07-09
Alright, I'll give that a go. I'll report back with results. Thanks for your time

---

### Post by Yellow Pasque on 2009-07-09
The correct driver (snd-hda-intel) is loaded. Most likely, you need to:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
and add this line:
```
options snd-hda-intel model=<MODEL>
```

where <MODEL> = something from the list below (e.g. medion-md2)

```
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targs/MSI with 2-channel
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  auto		auto-config reading BIOS (default)

```

---

### Post by Abdus on 2009-07-09
This, Temüjin, got my sound recording working. Skype still refuses to cooperate, but I'll make him bow to your knowledge. :) Thank you.

---

### Post by daniel_gv93 on 2009-07-10
i dont know where to search but i have like 4 hours trying to solve this problem.
I'm trying to record from my piano to the computer via line in, but I cant make audacity recognize line in to record, i tried connecting the cable in the mic jack, it works but at an horribly bad quality, i heard that line in is much better than microphone so i want to connect it there.
I tried also in the sound recorder and it doesnt record anything.
I tried enabling Line in as Output, just to hear the piano in the computer speakers, but it doesnt work either... i dont know what to do :confused:](*,)
Please any help will be gratefully taken...:-D

---

### Post by daniel_gv93 on 2009-07-10
oh and please excuse my bad english... im not a native speaker

---

### Post by Turtleman on 2009-07-10
> **Abdus said:**
> This, Temüjin, got my sound recording working. Skype still refuses to cooperate, but I'll make him bow to your knowledge. :) Thank you.

To make skype work, go on Options, sound devices, then go on sound in, then change it to w/e, then do the test call, then keep doing it till u find the right one. Then it will work perfectly.

---

### Post by Turtleman on 2009-07-11
> **Temüjin said:**
> The correct driver (snd-hda-intel) is loaded. Most likely, you need to:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
and add this line:
```
options snd-hda-intel model=<MODEL>
```

where <MODEL> = something from the list below (e.g. medion-md2)

```
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targs/MSI with 2-channel
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  auto		auto-config reading BIOS (default)

```

I have a Compaq Presario, and I tried auto-config but I didn't see any difference. Could you advise me on what model should I put?

Thanks

---

### Post by Yellow Pasque on 2009-07-12
My guess would be one of these models
```

  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig  3-jack 6-channel with SPDIF I/O
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)

```

---

### Post by Turtleman on 2009-07-12
> **Temüjin said:**
> My guess would be one of these models
```

  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig  3-jack 6-channel with SPDIF I/O
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)

```

Mine has 3 entrances in the back (mic, sound out, line in). But how do I know if it is 6 channel or SPDIF I/O?

---

### Post by Turtleman on 2009-07-13
Bump

---

### Post by Yellow Pasque on 2009-07-13
> But how do I know if it is 6 channel or SPDIF I/O?
Look at your system specs. For SPDIF, do you have a jack for digital audio?

If you're completely unsure, try all of them.

---

### Post by Turtleman on 2009-07-13
> **Temüjin said:**
> Look at your system specs. For SPDIF, do you have a jack for digital audio?

If you're completely unsure, try all of them.

Humm, it must be 3 jack SPDIF or w/e, because it has only 3 entrances in the back. I'll try it out.

---

### Post by Turtleman on 2009-07-13
> **Temüjin said:**
> My guess would be one of these models
```

  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig  3-jack 6-channel with SPDIF I/O
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)

```

Tried all of those, but none of them got the result I expected. Do you have any other suggestions?

---

