---
title: "midi controller keyboard M-AUDIO Keystation 49 Mk2"
date: 2015-12-09
forum: Multimedia Software
---

### Post by fangorn2 on 2015-12-09
Is it supported by Ubuntu?
It is described as plug & play for both Mac and pc, that's why I  guess it should, but I could not find specifications for Linux.
What eventually would you suggest as a midi controller for a newbie? I thought that the more keys the better, but I could be wrong.

I would like to make audio and video.
What applications would you recommend to use?
Would eventually be a good idea to use a live Ubuntu Studio?

---

### Post by yoshii on 2015-12-14
When you are shopping for a MIDI controller or even a USB audio interface, look for the term:  **USB Class Compliant**
This will mean that no drivers are needed to be installed for the hardware, and it will use the OSes built-in generic system.  

I bought the Alesis Q25 USB MIDI Controller and the Alesis M1Active 320 USB Audio Interface/Powered Monitors for this reason.  
I believe the Alesis Q49 USB MIDI Controller is also USB Class Compliant.  49 keys is definately a lot better.  I wish that I hadn't gotten 25 keys; 49 allows real music to be made on it.  25 is too limited.  

I use Ubuntu Studio because it's designed for audio/video use.  I recommend using the LTS (long-term supported) version of it (v14.04.3 at this time).  It will be upgradeable to the next LTS version in April.  
If you are still unsure about the keyboard, contact the manufacturer via email or 1-800 telephone number and ask them if it's USB Class Compliant.  

For video applications, Ubuntu Studio comes with a few different types.  I don't know that much about them; Kdenlive seemed to be the most stable when I last checked.  Also freeware AVIdeMux is available from the internet, but it's just a simple splicer.  

For audio, Ubuntu Studio also comes with a few different types and you can install the KXstudio repositories on top of Ubuntu Studio to get more updated versions.  Just be sure to follow the instructions on the KXstudio website.  

I actually don't use many Linux programs on mine.  I use Audacity and OcenAudio, but for everything else I use Windows programs running in Wine.  Ubuntu Studio comes with Wine.  
I run Reaper and EnergyXT, both using the 32-bit Windows versions.  

But be aware that to get better results, I had to implement some DAW configurations/optimizations/tweaks for Linux.   But that is kind of a different topic.  
But for starters, I chose to format the drive during installation as ext3 and I created a swap space that wasn't inside of an extended partition like the default, but instead a dedicated partition of it's own.  
I disabled unneeded services and features and had to experiment with certain Reaper configuration settings.  EnergyXT beta3 for Windows turned out to be easier to run even though it's not as supported as Reaper.  But Reaper is more powerful.  

There are some guides out there on the internet for optimizing and tweaking Linux for DAW use, and that's what I had to refer to.  Sorry I can't think of the exact sites off the top of my head.

---

