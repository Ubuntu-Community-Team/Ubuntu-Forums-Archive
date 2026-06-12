---
title: "i have no audio when trying to play dvds"
date: 2009-08-12
forum: Mythbuntu
---

### Post by derrickadean on 2009-08-12
I need your help again guys 

                  I got the audio on the frontend working after getting the right alsa driver and then i got dvd playback by setting my dvd device (under video settings) to /dev/sro  everything works except for audio on dvd or dvd iso playback i get audio from a riped dvd what is thr problam there a difrercne in format. or could this be from the wrong alsa driver or something non related?

---

### Post by larsolav on 2009-08-13
Is the frontend running 9.04? I know from my own experience that the ISO playback is set-up to play using Xine, not the internal mythplayer as Xine does a better job at playing ISOs and DVDs (internal player often stalls at the copyright flash screen, typically on Disney movies...) Check to see if myth is set up to use Xine to play DVDs and ISOs, if it is, then you need to go to the audio settings in Xine and make sure you set it up correctly as well.

Cheers!

---

### Post by derrickadean on 2009-08-13
how would that explain why im not getting audio on any dvd playback from a disk under the frontend.  im sure its not running xine because i cant even get xine to playback dvd at all.

---

### Post by larsolav on 2009-08-14
> **derrickadean said:**
> how would that explain why im not getting audio on any dvd playback from a disk under the frontend.  im sure its not running xine because i cant even get xine to playback dvd at all.

Ah, well in that case I am over my head in water, and will eloquently butt out. Hopefully someone else may know why you are experiencing this weird behavior. Oh, one more thing before I butt out, does the frontend log say anything that may shed some light on the situation?

---

### Post by derrickadean on 2009-08-16
sory man i didnt mean to try and undermine your intelligence i just wont to make since of whats going on. i am new to linux and mythbuntu.  im getting a lot of information and cant make much since of it . i not only want this to work but i also want to know how it works               I would like your help                      

i found this   (to anyone reading this that is in tha same boat  as me look at these logs i didnt before thank you   larsolav)   

 2009-08-16 10:28:36.363 AudioOutput Warning: Mixer attach error -2: No such file or directory
            Check Mixer Name in Setup: '/dev/mixer'
2009-08-16 10:28:36.363 NVP: Enabling Audio
2009-08-16 10:28:36.368 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-16 10:28:36.368 Opening ALSA audio device 'default'.
ALSA lib control.c:909snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-08-16 10:28:36.378 AudioOutput Warning: Mixer attach error -2: No such file or directory
            Check Mixer Name in Setup: '/dev/mixer'


this is what it said about about my sound driver
*-multimedia
                description: Multimedia audio controller
                product: ES1371 [AudioPCI-97]
                vendor: Ensoniq
                physical id: 9
                bus info: pci@0000:01:09.0
                version: 09
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ENS1371 latency=96 maxlatency=128 mingnt=12 module=snd_ens1371

---

### Post by derrickadean on 2009-08-17
fixed it!! fixed it!! fixed it!!

i was over diagnoseing the problem. the problem was i was allowing ac3 and dts  data to pass threw my sound card. these are used for digital surround sound devices. in from the mythbuntu frontend go to utilities/setup>setup>general 
then uncheck the 2 boxes that allow this action
when i unchecked these the audio worked perfict

---

### Post by larsolav on 2009-08-18
> **derrickadean said:**
> fixed it!! fixed it!! fixed it!!

i was over diagnoseing the problem. the problem was i was allowing ac3 and dts these are for data to pass threw my sound card. these are used for digital surround sound devices. there are 2 check boxes in from the mythbuntu frontend go to utilities/setup>setup>general 
then uncheck the 2 boxes that allow this action
when i unchecked these the audio worked perfict

Well, um, that was going to be my next suggestion...:lolflag:
Glad you got it fixed!:P

---

