---
title: "Again, software updater followed by reboot kills sound from built-in speakers"
date: 2023-02-08
forum: Multimedia Software
---

### Post by cigtoxdoc on 2023-02-08
Software updater installed Linux kernel 5.19.0-31-generic and other updates.  It required a reboot.  Sound (built-in speakers) that had been working all day on my Dell Precision 7720 stopped working.  The CL pactl info gives the output if the sound is working or not.  Pulse audio volume control shows the input from Firefox streaming internet radio.  Plugging the jack from my external sound system gives sound.  Removing the jack does not return the sound to the built-in speakers.

Since I do not have the luxury of external sound systems at all my work locations, I am hoping the experts on pipewire and pulse audio will provide a list of commands or other diagnostic tools they would like me to run to fix this problem.  Also, two weeks ago, plugging in the same external speaker system that is working now, did not work back then.

On one of the reboots this evening, the fine print that flashes up during the boot process mentioned something about a blocked hardware interrupt.

Thank you,

John

---

### Post by cigtoxdoc on 2023-02-09
I hope the moderators will put some expertise on this problem.  Another strangeness: Rhythmbox will play correctly to the built-in speakers of Studio Brussels, Belgium, for example; or WUVT-FM.  

Thank you,

John

---

### Post by cigtoxdoc on 2023-02-14
Please, more help still needed.  After two days of perfect operation, including warm and cold boots, I have no sound again with built-in speakers on my Dell 7720 laptop.  I have tried all the suggestions in this section and I still do not have sound.  John

---

### Post by andrewt144 on 2023-03-05
I have the same problem with Asus HDMI. After last update previously working outputs disappeared from aplay -l 

lspci shows hardware and dmesg shows both HDMI connectors loading. But alsa just ignoring them.

What gives?

---

### Post by cigtoxdoc on 2023-03-05
At some point, system architecture changed so that wireplumber must be installed when sound is done with pipewire, at least for laptops such as my Dell Precision 7720.  On the other hand, my hp 840 g1 laptop runs very nicely with alsa.  OS in both cases is Ubuntu 22.10 with Unity 7.6

---

