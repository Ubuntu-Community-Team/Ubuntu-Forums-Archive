---
title: "CLI help with Jaaa"
date: 2015-11-06
forum: Multimedia Software
---

### Post by expatver on 2015-11-06
Running 14.04LTS on a newly built Asus Z97 Mk1 motherboard. Audio chip is Realtek- lspci  shows 00:1b.0 Audio device: Intel Corporation Device 8ca0.  Further information on the sound device is
 Card: HDA Intel PCH                                                Chip: Realtek ALC1150 

from /proc/asound/cards (looking at system information  in CLI alsamixer)

proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH         
                     HDA Intel PCH at 0xdf430000 irq 45
 1 [NVidia         ]: HDA-Intel - HDA NVidia           
                      HDA NVidia at 0xdf080000 irq 18 

The NVidia  sound device is the graphic card, an EVGA GEForce GTX750TI  driving a pair of Benq monitors (one of the monitors uses HDMI and  the audio channel to the speakers in the second monitor also works when selected). 

I have  installed qpaeq, a FFT graphic eq. Everything works.

I installed Jaaa  with ALSA support from Synaptic. 

What I am trying to do is enable Jaaa where I can see the output from the audio stack to the sound card. I have spent several hours trying different CLI options. All that Jaaa will see is  noise from the capture channels in the ALSA mixer, nothing more. 

I suspect that Jaaa may not work with Pulse audio running or that I am using the incorrect CLI options. 

Any suggestions would be appreciated.  I have used Linux for  a number of years and thought I understood CLI but have hit a dead end with this.  

Regards

Expat

---

