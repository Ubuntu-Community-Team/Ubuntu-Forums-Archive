---
title: "Sound card with Multiplexer/Multi Out"
date: 2014-05-09
forum: Multimedia Software
---

### Post by thenh813 on 2014-05-09
I have a sound card that can output audio to the Line In and Microphone jacks as well as Line Out. It never works on Ubuntu, even when I try to force audio output through those ADCs. It is a unspecified ICH5/Soundmax type chip on the Intel D865GBF Motherboard. It also has input via a four pin header on the MB and with the front panel headphone/microphone ports, and those do work. I think some special code must be sent to the card's controller address (in RAM) but I am not sure, anyone have a similar card? Also I the Line In/Microphone ports can be used interchangably with the change of a slider in the SoundMax Extreme control panel on Windows XP. It can also put out boosted stereo LFE channel on the Microphone port as well (this does work, although it does not know the MIC and LFE are the same so it causes wierd bugs in Audacity). I finally moved completely to Ubuntu after the support ended and keep XP in a VM only for use with the scanner (LOL I know, but there are no Lexmark X23XX drivers for Linux). I need surround output (two channels per jack, three jacks) like I had before, I never noticed this as I usually used headphones or stereo speakers for the past year. I want to watch TV (tuner card works fine haha!) in 6.3 Surround (6 speakers, 3 subs) otherwise I will be forced to buy a new sound card. I may have 6 PCI slots and 1 AGP, but I really dont think the MB's voltage regulators can take too much more addons. I currently have a Realtek Gigibit ethernet adaptor and a high speed Dialup modem supporting up to 115000 buad installed and the regulators sit around 180F. I may add a heatsink, but they are rated to 300F. Also the Ubuntu version I am using is 12.04 (certain hardware I have cannot run on newer kernels, I know that AS A FACT). I need help, but this isnt a rush situation, it just makes me depressed. :(

Thanks in advance,
----------------------TheNH813

---

### Post by thenh813 on 2014-05-14
Hello? Replies please LOL.
Sorry for bumping this, but it ended pretty far back and was no longer on the first few pages. Does anyone know anything about this or a similar situation? I would like to know if a need a new sound card or if there is a setting change/driver patch required. I might install XP again for playing DVDs and disable the Ethernet card in device manager to keep it disconnected. I will wait another four days before giving up and using Windows or buying a new card.

---

### Post by Yellow Pasque on 2014-05-15
Start here: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> even when I try to force audio output through those ADCs
How did you attempt that? hdajackretask?

---

### Post by thenh813 on 2014-07-04
Wow, I havent logged in for a while, sorry for seemingly forgetting  about this. You see, I accidentally discovered how to work the controls  when setting the output gain higher in alsamixer. 

If you compile Audacity  right, you have output hw#,# which you can force to be the output.. As to the question about jack, my Audacity DOES in fact use jack so it  probabally uses hdjackretask or a similar software function.

Here's a screenshot showing every setting of alsamixer.
[IMG]http://s18.postimg.org/tsf02mm1l/screenshot_000.png[/IMG]
[IMG]http://s17.postimg.org/fnshmvc7z/screenshot_001.png[/IMG]
 Missed the last option so another screenshot here:
[IMG]http://s9.postimg.org/lw47t8dpb/screenshot_002.png[/IMG]
Alsamixer sure has a few options with my card. Gotta make sure I set V_REFOUT to 0 so I dont feed speakers static voltage.

I  just love this old MB, it has so many features for its age. Its massive  though, weighs AT LEAST 9 pounds and is ATC (11.5in*9.5in). The amount  of outputs the sound has is amazing it even has a sound header on the MB  that acts as another stereo output. It also a a CD player in header for  the DVD drive.

I have been using Puppy Linux lately, but the same applies for Xubuntu.
I am running what I call 6.3 surround now, three sets of stereo speakers with subwoofers.

Here  is info for the board you might find interesting:  [http://downloadmirror.intel.com/15207/eng/D865GBF_D865GLC_TechProdSpec.pdf](http://downloadmirror.intel.com/15207/eng/D865GBF_D865GLC_TechProdSpec.pdf)

Once again sorry for never seeing you replied. Have a nice day.
-TheNH813

---

