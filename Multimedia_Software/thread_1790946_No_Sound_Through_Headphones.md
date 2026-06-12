---
title: "No Sound Through Headphones"
date: 2011-06-25
forum: Multimedia Software
---

### Post by agwest on 2011-06-25
Ubuntu 10.04 LTS
Card: HDA Intel
Chip: Realtek ALC889

I am completely stuck trying to get my headphones working on my computer. My headphones work, but not via my computer...my sound does work through my speakers... in alsamixer i see headphones at 00 but I can't change the levels... any help or information you need please respond and I will post back asap...

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbff4000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfb5fc000 irq 17


Thank you.

---

### Post by Veritas_08 on 2011-06-26
You mean you ran "alsamixer" on the Terminal or used the GUI for it?

In Terminal, you run the alsamixer command and a graphic shows up with your volume levels. From there just use your directional keys to select the slider to move. then up and or down. 

Also, at least you get sound lol I've no sound since I installed Natty on Monday. I'm working on it. I also have an intel sound card and while Ubuntu sees it it's just not using it it seems. Bummer. 

Best of luck to you!

---

### Post by agwest on 2011-06-26
> **Veritas_08 said:**
> You mean you ran "alsamixer" on the Terminal or used the GUI for it?

In Terminal, you run the alsamixer command and a graphic shows up with your volume levels. From there just use your directional keys to select the slider to move. then up and or down. 

Also, at least you get sound lol I've no sound since I installed Natty on Monday. I'm working on it. I also have an intel sound card and while Ubuntu sees it it's just not using it it seems. Bummer. 

Best of luck to you!

I ran alsamixer from the terminal. I see the headphone bar and it is green at 00, but I can't adjust it...

---

### Post by lidex on 2011-06-26
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

