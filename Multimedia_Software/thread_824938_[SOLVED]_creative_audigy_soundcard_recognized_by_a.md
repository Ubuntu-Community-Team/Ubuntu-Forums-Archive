---
title: "[SOLVED] creative audigy soundcard recognized by alsa yet no sound"
date: 2008-06-10
forum: Multimedia Software
---

### Post by radical3 on 2008-06-10
[I]pentium 4, 3.0ghz
1gig ram
on board SIS SI7012 sound car [works]
pci creative audigy soundcard 
[/I]

ive installed alsa , alsa mixer gui, alsa mixer, yet no sound at all
when i go system > preferences > sound .........audigy1[SB0090](alsa mixer) shows up under "default mixer tracks", but nowhere else.:confused: 

"SIS SI7012" (my onboard) shows up in every drop down box and i can use it for all my sounds, music , video, even flash (youtube and such). yet it wont play any system sounds like log in and log out sounds, i still get system beeps:confused:. 

ive searched the forums but havent found a solution. 

pls help.:(

---

### Post by biohypnotix on 2008-06-10
I had a similar issue with my Audigy 1. This worked for me.

Go to Volume Control, then the Switches tab, and untick Analog/Digital output jack box.

---

### Post by radical3 on 2008-06-10
thanks worked* i had to do some other things because i had everything configured to use the on board. 

heres what i did
1. i right clicked the sound icon on the top right of the screen and selected "open volume control" it was set to my on board i changed it by going to **FILE **> **CHANGE DEVICE** and then i selected audigy

2. i went to the switches tab located in the same window (volume control)  and unchecked audigy analog/digital output jack, i then went to youtube.com to play a video to test the sound.
*-----side note i also have PULSE AUDIO DEVICE CHOOSER installed a nice sound application which allows you to choose where your sound is directed to, it helped me get sound in firefox with flash i will explain that after.------*.........no sound

3. i went to **APPLICATIONS > SOUND & VIDEO > PULSE AUDIO DEVICE CHOOSER** which put a small icon to the top right of my screen, i left clicked the icon and selected VOLUME MANAGER . it showed up that i was playing a flash video(youtube) and displayed left and right volume control, i right clicked the left and right volume control and changed the stream  from my onboard to my audigy soundcard which showed up as **standard pcm playback**.youtube instantly began giving sound.:)

4. mp3's and other media applications were giving no sound, so i right clicked the sound icon on the top right of the screen and selected "open volume control" the device was still set to audigy and i realized that PCM (my **standard pcm playback**) was muted. i unmuted  it and [SIZE="5"]BOOM[/SIZE] sound:). everything works EVERYTHING log on log off everything.


no flash sound in firefox
easy
1.download PULSE AUDIO DEVICE CHOOSER simply go to the add remove programs option located at the bottom of the applications menu , in it , at the top centre there is a drop down menu change the option to "all available applications" and type "pulse" in the text box download the 5 PulseAudio programs the when installed follow step 3. &.4 of my above solution. 



[SIZE="3"]**_can a [mod] please add the word [COLOR="DarkRed"][SOLVED][/COLOR] to this thread title thanks_**[/SIZE]\\:D/

**[COLOR="DarkRed"]btw thanks a bunch biohypnotix[/COLOR]**

---

### Post by xc3RnbFO8P on 2008-06-10
> can a [mod] please add the word [SOLVED] to this thread title thanks
Do it your self, in **Thread Tools**

---

### Post by radical3 on 2008-06-10
didnt know i could do that

---

### Post by Cenema on 2008-07-06
Hi,
   I'm having quite the same problem, I'll open an other post cause it seems that none is reading this (cause of the "SOLVE" in the post' title)

---

### Post by m0j0-j0j0 on 2008-07-12
> **biohypnotix said:**
> I had a similar issue with my Audigy 1. This worked for me.

Go to Volume Control, then the Switches tab, and untick Analog/Digital output jack box.

Genuis, after days of mucking around, found this and it works a treat. Thank you very much :)

---

### Post by Ed J on 2008-07-16
> **m0j0-j0j0 said:**
> Genuis, after days of mucking around, found this and it works a treat. Thank you very much :)

Where did you find it?

---

### Post by strangeattractor on 2008-09-25
This helped me get sound working for using Flash in Firefox.  Thank you.

---

