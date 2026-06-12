---
title: "sound problem"
date: 2009-04-02
forum: Multimedia Software
---

### Post by wombil on 2009-04-02
Hello Every one,I have a problem.
I have ubuntu 8.04 , alsamixer tells me I have        sound card,VIA 8235,
chip       Realtek ALC655 Rev 0
Sound works well on CD player,skype and evolution e-mail attachments.
Sound also works well in all applications on xp installed on separate hdd on same pc.
Where should I start looking to fix this?
All help appreciated,thankyou.

---

### Post by xc3RnbFO8P on 2009-04-02
> Sound works well on CD player,skype and evolution e-mail attachments.
Sound also works well in all applications on xp installed on separate hdd on same pc.
What doesn't work?

---

### Post by wombil on 2009-04-02
Sorry about thal.Left out the main thing.
Problem is that I can get no sound from you tube or similar applications.

---

### Post by xc3RnbFO8P on 2009-04-02
Did you check Volume Control?
Master, PCM

---

### Post by wombil on 2009-04-02
Yes done that.

---

### Post by alexandari on 2009-04-02
hmm are you listening or using some "sounds" (that sounds dumb xD) when you`r opening youtube? and are you using ALSA on the Sound Events Music and Movies Audio Conferencting and all those? 
 
1.sudo apt-get install alsa-oss    (or you can find in Synaptic Package Manager)

after you install it open the terminal and type: 

aoss firefox

open youtube and tell me if there`s any sound

---

### Post by xc3RnbFO8P on 2009-04-02
Try:
**sudo update-flashplugin**

---

### Post by wombil on 2009-04-02
Thanks Alexandrei but that didn't fix it.Got to go to bed now so I'll try later.thanks ringi too

---

### Post by wombil on 2009-04-02
Thanks Ringi,
typed "sudo update-flashplugin" in terminal,and it asked for password,I entered it and terminal came back with,"sudo: update-flashplugin: command not found".

---

### Post by wombil on 2009-04-02
Latest move.
I just ran puppu linux 4.1.2 live and everything sounds ok.
Still no sound in ubuntu.

---

### Post by wombil on 2009-04-03
well guys I've tried all the remedies I could find in these pages but none seem to work for me.Maybe I should install a pci sound card.I have a msi PM 400 socket A motherboard.Any suggestions?

---

### Post by eye208 on 2009-04-03
Your current soundcard is not the culprit. Realtek cards are widespread and well supported by ALSA. Your problem with missing sound in Flash apps is caused by PulseAudio. If you do a search in this forum, you'll find hundreds of threads dealing with the same problem. It has been a frequent issue since Ubuntu 8.04.

The good news is that you can remove PulseAudio and have all your apps play sound through plain ALSA. I did that last year and never looked back.

---

### Post by wombil on 2009-04-03
Thanks EYE 208.I tried both methods in "Fix pulseaudio in 5 minutes" but still no sound.I then removed all reference to pulseaudio in synaptic.Still nothing.
Using the test boxes in,System>preferences > sound and all devices set to alsa I get no sound from any of the tests.
I do get sound from the tests with;
ES 1371 DAC1  and 
ES 1371 DAC2/adc
If I want sound I have to go back to windows.

---

### Post by eye208 on 2009-04-03
> **wombil said:**
> I do get sound from the tests with;
ES 1371 DAC1  and 
ES 1371 DAC2/adc
If I want sound I have to go back to windows.
If you have two soundcards in your computer, ALSA will initialize them in random order. I guess that the Realtek card was chosen as default, but the Ensoniq card is the one you are actually using.

In this case the solution is simple: Deactivate the unused Realtek card in the BIOS, so that ALSA chooses the other card as default.

---

### Post by wombil on 2009-04-04
Thank you Eye 208.problem fixed.Just disabled AC 97 in bios and all ok.Never had this trouble with other installations before tho.I suppose if I remove the pci card would do the same thing?
Thanks to all other helpers too.

---

