---
title: "Old sound card problem"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by haseeb on 2007-06-03
I have started linux by installing suse 9. after experimenting few distros i am now stable in ubuntu. 
from the very first day i am facing a somewhat bizarre problem with my soundcard. my sound card
is built in to the motherboard and its model number is **82801BA/BAM AC'97 Audio**. all the distros
i have installed think i am using a headphone. in the volume control only **headphone** bar is active. as
as result my hifi sound system give me a very low volume poor quality sound. I have tested with another sound
card inserted in one of my pci slot and it works perfectly. 

anyone here to give me a suggestion by which i can hear sound perfectly from my ubuntu pc?


n.b. plz dont give any suggestion like 'check you speaker cable rightly inserted in the soundcard ports.'

---

### Post by pseudonym on 2007-06-03
Type 'alsamixer' in a terminal (or use Gnome ALSA mixer/Kmix) and make sure the outputs you want are all unmuted.

---

### Post by haseeb on 2007-06-03
everything is unmuted. to increase vol i can use the headphone bar ONLY. others donot work.

---

### Post by pseudonym on 2007-06-03
That's a fairly old sound chip, but that kind of thing is usually well supported by ALSA. My only advice if you can't see any configuration errors is to just disable the onboard sound and use a cheap PCI card instead like an older model Soundblaster or C-Media card.

---

