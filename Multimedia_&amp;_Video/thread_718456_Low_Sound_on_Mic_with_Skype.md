---
title: "Low Sound on Mic with Skype"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by Epiphyte on 2008-03-08
I have just installed Skype V 1.4.0.118 under Ubuntu V7.10. This is a dual booting system, so I have results to compare against Windoze. I am trying to migrate the environment to Ubuntu (in order to *scrap* Win XP).

The hardware has a SiS SI7012 on the motherboard and has a Realtek AC97 card installed. 

I am having problems getting reasonable volume from the microphone on a Skype test call - all I get is a *very soft* replay. (this all works perfectly under Skype under WinXP). 
I have installed the Gnome ALSA mixer to allow better control over the audio card, and checked that I have 20dB boost on the mic turned on.

I have selected SiS SI7012 MIC ADC for Sound Capture in System>Preferences>Sound, but when I click "test" I get the following response:
> 
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

Can anyone please help me with this? :confused:

Thanks in advance.

---

### Post by s1mmel on 2008-03-08
> **Epiphyte said:**
> I have just installed Skype V 1.4.0.118 under Ubuntu V7.10. This is a dual booting system, so I have results to compare against Windoze. I am trying to migrate the environment to Ubuntu (in order to *scrap* Win XP).

The hardware has a SiS SI7012 on the motherboard and has a Realtek AC97 card installed. 

I am having problems getting reasonable volume from the microphone on a Skype test call - all I get is a *very soft* replay. (this all works perfectly under Skype under WinXP). 
I have installed the Gnome ALSA mixer to allow better control over the audio card, and checked that I have 20dB boost on the mic turned on.

I have selected SiS SI7012 MIC ADC for Sound Capture in System>Preferences>Sound, but when I click "test" I get the following response:


Can anyone please help me with this? :confused:

Thanks in advance.


Get into your console and type in 

alsamixer

just boost up every channel you find there :popcorn:

---

### Post by Epiphyte on 2008-03-09
Hi s1mmel,

That seems to work!

I did that and found that the "Capture" setting was set very low. (A bit counter-intuitive but I worked it out.)

Thanks.

---

