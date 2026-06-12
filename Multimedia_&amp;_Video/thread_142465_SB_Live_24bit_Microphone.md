---
title: "SB Live 24bit Microphone"
date: 2006-03-10
forum: Multimedia &amp; Video
---

### Post by Snipe3D on 2006-03-10
Well, I got my SB Live working flawlessly, all except that no capture tab shows up in volume control, and so I cant use my microphone. I set it up using 
[http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307)
Which details how to set up alsa+ubuntu+sblive24bit ca0106 module.

Any ideas? Both sinks are set to alsa.

---

### Post by Stealth on 2006-03-10
What I have to do is open a terminal, type in "alsamixer"
Then in there press tab, and there will be the capture section, look for ur mic, unmute it and crank it up! :D

---

### Post by Snipe3D on 2006-03-10
hmm..i cant seem to unmute or adjust volume..
[http://x10.putfile.com/3/6813411041.png]("http://x10.putfile.com/3/6813411041.png")

i hit m or try , and . but has no effect, arrows dont change anything either. i tried the i2s in as well, no effect.

---

### Post by Snipe3D on 2006-03-11
any ideas?

---

### Post by Snipe3D on 2006-03-12
I tried installing drivers according to [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1")
(The ALSA project instructions) but when I go to alsamixer, it is still using CA0106 as my sound card.

/proc/asound/cards also shows CA0106 as soundcard 0, even though i set up the driver as emu10k1...

any ideas?

---

### Post by JustRandomName on 2006-03-12
Is your SB Live! usb or PCI?

---

### Post by Snipe3D on 2006-03-12
Pci

---

