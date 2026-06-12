---
title: "Spectrogram? Audacity? Any other recomendations?"
date: 2010-12-18
forum: Multimedia Software
---

### Post by gabriella on 2010-12-18
Hi all.

I just installed Audacity. I'm totally new to it so may be missing something but I'm unclear where it allows spectrogram analysis of the microphone audio input or just of an already created file. Can someone clarify please?

How about any other recomendations for a suitable application? I'm going to be doing some voice training and need something that can give me a live spectrogram of the microphone input as its happening.

Thanks :)

---

### Post by gabriella on 2010-12-19
anyone?

---

### Post by cchhrriiss121212 on 2010-12-19
I think Audacity can only handle pre-recorded spectrograms. To do that just click on the track drop down menu and select Spectrum, more info here:
[http://manual.audacityteam.org/index.php?title=Spectrogram_Preferences](http://manual.audacityteam.org/index.php?title=Spectrogram_Preferences)

If you want live visualisation you will have to use the jackd sound server with the Invada LV2 plugin loaded in the lv2rack program. This is a little more complicated as jack is designed for more pro-quality work.
Here is a list of the packages to download from synaptic:
jackd
qjackctl
patchage
invada-studio-plugins-lv2
zynjacku
(Plus any dependencies these packages require)

During jack installation you will be asked if you want to set up realtime access, agree to this.

First open up jack control from your audio applications menu and press start. Use the setup window to adjust the latency or select a non-default sound card. Now open up lv2rack and go to Effect>Load and select the Invada Meter plugin. Open up patchage and connect your system capture port to the lv2rack port.

---

### Post by gabriella on 2010-12-20
> **cchhrriiss121212 said:**
> I think Audacity can only handle pre-recorded spectrograms. To do that just click on the track drop down menu and select Spectrum, more info here:
[http://manual.audacityteam.org/index.php?title=Spectrogram_Preferences](http://manual.audacityteam.org/index.php?title=Spectrogram_Preferences)

If you want live visualisation you will have to use the jackd sound server with the Invada LV2 plugin loaded in the lv2rack program. This is a little more complicated as jack is designed for more pro-quality work.
Here is a list of the packages to download from synaptic:
jackd
qjackctl
patchage
invada-studio-plugins-lv2
zynjacku
(Plus any dependencies these packages require)

During jack installation you will be asked if you want to set up realtime access, agree to this.

First open up jack control from your audio applications menu and press start. Use the setup window to adjust the latency or select a non-default sound card. Now open up lv2rack and go to Effect>Load and select the Invada Meter plugin. Open up patchage and connect your system capture port to the lv2rack port.

OK thank you for the information and instructions. I will take a look at this. Yes my project does need analyse the microphone input live as its being spoken/sung

---

### Post by gabriella on 2010-12-28
Are there any other candidates besides jackd sound server to give live visualisation of the mic input??

---

### Post by cchhrriiss121212 on 2010-12-28
Nope, anyone using Linux audio for editing/producing will be using jack. Are you having trouble with it?

---

### Post by gabriella on 2011-02-24
> **cchhrriiss121212 said:**
> Nope, anyone using Linux audio for editing/producing will be using jack. Are you having trouble with it?

Sorry for leaving it so long..
No I have it installed successfully and seems to do what I want.

The only slight criticism I have is that there are various parts to the whole application and sort of junks up the Sound/Audio menu and also that I have to start a new view each time I use it. However, that said it seems to do what I want and is certainly better than having to run a Windows one using WINE. I guess U was hoping for a single app like audacity which would do it all and simply. But doesn't seem to exist.

Anyway thanks!

---

### Post by cchhrriiss121212 on 2011-02-24
A few weeks back I found Baudline which works with or without jack:
[http://www.baudline.com/](http://www.baudline.com/)
It is not exactly user friendly, though it is very accomplished in terms of features.

---

### Post by gabriella on 2011-02-25
> **cchhrriiss121212 said:**
> A few weeks back I found Baudline which works with or without jack:
[http://www.baudline.com/](http://www.baudline.com/)
It is not exactly user friendly, though it is very accomplished in terms of features.

OK thanks..
I only just looked at the link when I saw your reply. Yes it does look quite complicated, and I'm not an engineer or anything. But will have to read more about it. I'm just starting my voice coaching but your initial sugestion is definately better than the Windows app.

---

