---
title: "Hoontech DSP24 ADC&amp;DAC2000 problems"
date: 2007-05-21
forum: Multimedia Production
---

### Post by mb123 on 2007-05-21
My problem is that the sound card (DSP24 MKII using ICE1712 Drivers) shows up fine and the system sounds work. Everything seems to work but when I go to input my guitar or whatever through the ADC&DAC2000 I can't get an input for anything. I have tried most of the "tricks" already as far as unmuting channels etc. I have tried the. ALSA mixer, ENVY24 and nothing seems to work.
The input channel LED's on the ADC don't light up to show that the different channels are engaged. 
The hardware works under Windows XP and works under Musix  but I can't seem to get it to work in Ubuntu Studio. I haven't seen any other similar posts for this card. 

P4 2.4 GHz, 1GB RAM with Hoontech DSP24 MKII PCI Sound Card with ADC&DAC2000 8 channel input output module.
Am I dead in the water with this setup?
Any suggestions??

Thanks in advance:D

---

### Post by huwshimi on 2007-05-23
Hi. I have the same card with a c-port breakout box (I'm pretty sure it's exactly the same thing). I had the same problems. What I had to do was change the switches on the side of the breakout box so that it was on 1 (one) (before that it was on 2) and then it worked perfectly.

I hope that helps. If you can let us know either way that would be awesome.

Cheers.

---

### Post by mb123 on 2007-05-23
I looked at the DIP switches and they are already set for 1. I tried setting it for a few different numbers and it still does the same thing. Thanks for your help though. If you have any other ideas please let me know. Thanks again. :D

---

### Post by huwshimi on 2007-05-23
Do you have an onboard sound card? If so have you tried disabling it?

"The input channel LED's on the ADC don't light up to show that the different channels are engaged. " This is what worries me... They should be on, and if I remember correctly they went on when I changed the card to 1 (only the 1 switch is on and the rest are down on mine).

Cheers.

---

### Post by mb123 on 2007-05-23
I do have an onboard sound card and I disabled it in the Bios. The switches on the side of the card are configured the same as yours, number 1 on and the rest off.
I guess the thing that is really confusing me is that everything works in the Musix operating system which is similar to Ubuntu Studio and has the same prgrams i.e. Jack, Ardour etc. When Musix starts up all input LED's are on from the beginning. There must be some kind of configuration file I need to play with to get it to work.
In [COLOR="Red"]Windows[/COLOR] everything works fine too.
I am definitely at a loss.

Thanks for your help. :D

---

### Post by nuvolablues on 2007-05-25
Hi mb123
I've seen your post is not dated but I just wanted to ask you if you finally got to make your HOONTECH soundcard work. 
I swithced to Ubuntu since a few days and I can make my HOONTECH DSP24 work yet. when I succeed in listening any sounds I don't have the control of volume, everything sounds at the highest volume and inputs don't work.

What should I do?
if you got any idea pleas tell me!!
thank you

BYE

---

### Post by mb123 on 2007-05-25
No luck yet. I will definitely let you know if I get it solved.

:D

---

### Post by huwshimi on 2007-05-25
> **nuvolablues said:**
> when I succeed in listening any sounds I don't have the control of volume, everything sounds at the highest volume

You could try installing alsa-tools-gui (in Synaptic) and then run (ALT+F2) and type in "envy24control" and try playing around in there to change the volume.

Cheers.

---

### Post by nuvolablues on 2007-05-30
> **xi0nblue said:**
> You could try installing alsa-tools-gui (in Synaptic) and then run (ALT+F2) and type in "envy24control" and try playing around in there to change the volume.

Cheers.

I did it but still have no control on any volume, I can hear direct input but no control on output

---

### Post by leinez on 2007-06-06
hey guys
first I would say sorry for my worse english...
I am from Germany and I have same soundcard as you...
Hoontech audio dsp 24 + ADC&DAC2000

I have the same problems:
The Output works but I have no control  at the volume...
The Inputs do not work...the light over the Inputs doesnt shine....

The switches on the right side: Nr. 1 is at "on" and all others are at "off"...

but I have a link for you:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Hoontech&card=Soundtrack+Audio+DSP+24.&chip=ICE1712+%28Envy24%29&module=ice1712](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Hoontech&card=Soundtrack+Audio+DSP+24.&chip=ICE1712+%28Envy24%29&module=ice1712)

scroll down to "Notes"

I have tried it but it doesnt work...
But it is possible that I cant do this because of my worse English...

If you find a solution pleas let me know...

thanks and greets
leinez from germany (on ubuntu-studio feisty)

---

