---
title: "Can.t play music from diferent applications in the same time."
date: 2008-04-27
forum: Multimedia Software
---

### Post by qbox on 2008-04-27
Hi
I cant play music from different application on the same time. If I play music from amaroc I cant play music from Last.fm, VLC or from youtube in the same time. some applications give me the message that another application use sound device or I dont have sound device. Amarok is given like an example. Any application can play mysic but in the same time another application cant.
Any idea?
Thank you all
Dell Inspiron 1520 ALSA sound card.

---

### Post by citizenc on 2008-04-27
The easy way to fix this is to force Ubuntu to use the ALSA audio device for all playback:

System -> Preferences -> Sound

Make sure all of the options under the "devices" tab is set for ALSA (it probably says "autodetect" right now or something).

---

### Post by qbox on 2008-04-28
I put all tabs on ALSA but still not working :(

---

### Post by qbox on 2008-04-28
I try somethings and now I have audio when I mix some applications. But now i have problem with Last.fm. If only this program must play music and another can't or opposite. Can somehow fix and this or not?

---

### Post by evertmantel on 2008-04-28
Suddenly had the same issue... 
The above solution didn't work for me immediately either.. 
After some fiddling it did, however:
 
What I did: check all the sounds. They all worked. After closing I still had the same issue. Then I selected the Default Mixer Track. HDA mixer Alsa and selected the Device to control with the volume button (Master).

And there is was!

Make sure on the Tab sounds "Enable Software Sound Mixing" is checked.

I suspect the WinXP is use under Virtual Box was the cause: I had the host audio driver set to Pulse, instead of Alsa.

---

### Post by qbox on 2008-04-28
I put all on pulse audio. I still have problem with Last.fm...

---

### Post by evertmantel on 2008-04-29
check if flash is installed and enabled (firefox>tools>add-ons>plugins>shockwave flash.)

If not, install flashplugin-nonfree with the synaptic manager (multiverse repository).

---

### Post by qbox on 2008-04-29
The plugin is installed. Im on 64 bit Ubuntu 8.04

---

### Post by evertmantel on 2008-04-29
Ran out of ideas... sorry. Anyone else..??

---

