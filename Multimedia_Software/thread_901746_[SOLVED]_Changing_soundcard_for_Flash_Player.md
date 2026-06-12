---
title: "[SOLVED] Changing soundcard for Flash Player?"
date: 2008-08-26
forum: Multimedia Software
---

### Post by choosebreakfast on 2008-08-26
Hello, I am looking for some help, and I have not found it in my previous searches through these forums or other forums. It took awhile, but I finally have Flash Player properly working on my Firefox. Now the problem is that it is playing through the soundcard in my laptop instead of the USB soundcard I have set up. Everything else on my system runs through the USB soundcard. The one inside the laptop just doesn't produce enough sound to make anything enjoyable. Is there anyway through terminal or otherwise to reroute the sound within Flash Player to go through my USB soundcard instead of the other? Thank you in advance

---

### Post by patrickballeux on 2008-08-27
Hi,

I came across that thread that would help you:

[http://ubuntuforums.org/archive/index.php/t-408453.html](http://ubuntuforums.org/archive/index.php/t-408453.html)

Basically, you reorder your audio device so the USB one will be first and then, detected (used) by the Flash player. (Look for the last comment...)

Good luck!

---

### Post by choosebreakfast on 2008-08-27
Thank you very much for you help! I hope it works!

---

### Post by choosebreakfast on 2008-08-27
Thank you, it did work, but for all the people that are as new as myself, there are some things left out of that post.

Here is what I had to end up doing:

In terminal, type:

less /proc/asound/modules

It should output your sound cards that the computer uses and their position. Copy and Paste these into a text editor, because you will need them later.

Then type:

gksudo gedit /etc/modprobe.d/alsa-base

or 

sudo nano /etc/modprobe.d/alsa-base

depending on what editor you want to use.

This will open your sound configuration file up in an editor. When it opens, scroll down to where it says "# Prevent abnormal drivers from grabbing index 0"

Below that it will have a string of lines that read
options saa7134-alsa index=-2
along with others. Now you want to force it to read the sound card you want it to first. For mine, it was snd_usb_audio

so if you can not find your card on the file, type in that area

options snd_usb_audio index=0

This will force it to read your USB soundcard first, you can also force it to order. Mine currently looks like this.

options snd_usb_audio index=0
options snd_hda_intel index=1
options saa7134-alsa index=2

Save it and then restart your computer and it should make it so Flash Player and other devices automatically play from the audio device you prefer.

---

### Post by hg21 on 2010-10-27
Thanks Choosebreakfast.

I spent a long time researching this before I found your excellent post. It's probably so long ago that you may never read this but I hope you do.  Thanks again.

---

### Post by yusbu on 2011-06-10
I have a stupid resolve for my ASUS M4A79 mainboard. I just did the code below and flash brought the sound back. It applies also when sometime sound didn't work because of multi sound hardware. My system is with Ubuntu, Debian Squeeze and Lenny. So I think the resolve is platform dependent, as long as your system use Alsa.

```
$ sudo alsactl init
```
Unknown hardware: "HDA-Intel" "Realtek ALC1200" "HDA:10ec0888,10438357,00100101" "0x1043" "0x8357"
Hardware is initialized using a guess method

More in detail,
```
$ less /proc/asound/cards
```
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbcf8000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfbffc000 irq 19

---

