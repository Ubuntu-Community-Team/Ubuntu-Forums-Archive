---
title: "Zotac nVidia Geforce GTX 460 HDMI audio not working"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by RaZoR1394 on 2010-09-21
Hi.

I got a Zotac nVidia Geforce GTX 460 768MB for my Core i5 computer recently. It seems to work ok with the Maverick beta except getting audio through hdmi. It works in Windows 7 and also with 9500GT+S/PDIF cable+Maverick. This 460 card isn't like the older nVidia cards that need a spdif cable coming out from the motherboard S/PDIF out, this has onboard audio but many of you probably already know that.

I use a hdmi receiver which is then connected to to my tv also by hdmi.

I can't find the onboard nVidia chipset on "#aplay -l" or in sound properties. All I seem to see is the motherboard chipset. Maybe the card is too new for Ubuntu (even beta)?

```

:~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: SB [HDA ATI SB], enhet 0: ALC889A Analog [ALC889A Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: SB [HDA ATI SB], enhet 1: ALC889A Digital [ALC889A Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

```

I use the 260.19.04 drivers from ppa.

edit:

It seems I found more info on this. I will investigate...

[http://www.nvnews.net/vbulletin/showthread.php?t=154755&highlight=hdmi+audio](http://www.nvnews.net/vbulletin/showthread.php?t=154755&highlight=hdmi+audio)

edit2:

Almost got it going now with 2.6.36-rc5. Just need to try it on the other computer.

```

aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: SB [HDA ATI SB], enhet 0: ALC889A Analog [ALC889A Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: SB [HDA ATI SB], enhet 1: ALC889A Digital [ALC889A Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 3: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 7: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 8: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 9: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

```

---

### Post by cariboo on 2010-09-21
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1566764&highlight=hdmi") thread, there is a proposed fix there.

---

