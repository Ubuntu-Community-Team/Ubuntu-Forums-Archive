---
title: "Howto configure Xonar D1 sound card"
date: 2011-12-13
forum: Multimedia Software
---

### Post by ericfahnoe on 2011-12-13
System: i386, Ubuntu 10.04 LTS with Asus Xonar D1 PCI sound card.
  alsa-base 1.0.22, alsa-utils 1.0.22 installed.

The rear card ports work fine but the front panel output is turned OFF in alsamixer. The front panel sound cable is connected to the card header, but I can't figure out how to enable this output. How can this be done?

I'd also like to be able to control some of the other card settings.  Any suggestions?

Thanks.

---

### Post by Mark Phelps on 2011-12-14
I used a new 5.1 soundcard for a while with a recent Cmedia chipset and found that the OSS app did a lot better job of configuring it and gave me more options.

You can read up on OSS at the link below:

[https://wiki.archlinux.org/index.php/Open_Sound_System]("https://wiki.archlinux.org/index.php/Open_Sound_System")

---

### Post by ericfahnoe on 2011-12-14
Thanks Mark. I will look into OSS for more configurations. Meanwhile I solved the front panel jack problem by toggling the m key (courtesy of Tommcd). Duh!

---

### Post by brett- on 2012-12-17
Well the Duh M-Key in alsa mixer worked for me on this card, problem solved.

---

