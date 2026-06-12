---
title: "Emu-0404 PCI"
date: 2010-05-10
forum: Multimedia Software
---

### Post by geeve420 on 2010-05-10
I have done a search and can't seem to get the info on how to get this sound card to work, all the posts I can find are a year or more old. I have just installed ubuntu 10.04. Can anyone please point me to some good info on how to get this thing working please!! 

Geeve

---

### Post by ajgreeny on 2010-05-10
Did it work in previous versions of ubuntu?  If so it should be possible to get it running in Lucid.

Check settings in ```
alsamixer
``` in terminal.  Levels often seem to be muted for some unfathomable reason at install of the system.

---

### Post by geeve420 on 2010-05-10
> **ajgreeny said:**
> Did it work in previous versions of ubuntu?  If so it should be possible to get it running in Lucid.

Check settings in ```
alsamixer
``` in terminal.  Levels often seem to be muted for some unfathomable reason at install of the system.

I'll check when I get home. I have never had it working in any version or distro of linux or ubuntu. I walked away from it about 2 years ago and thought I would try again as it seems alot more people are getting it to work. Thanks for the reply and I'll let you know if it was just muted.

I am kinda hoping it would work as it acts like it knows it is there, as far as showing an audio device. I have the onboard turned off in the bios so I assume it is seeing the emu. 

Thanks again

Geeve

---

### Post by geeve420 on 2010-05-10
I can click the speaker icon at the top by the clock and have choices of inputs and outputs but I have no sound at all. It is called PCM 2900 audio codec

Edit: Spent a couple hours on it last night. I do know for sure I have the emu that is coming back as (1102:0008 ), from what I have read it is the one that works. I installed alsa mixer and it sees no soundcards. I went to the ALSA matrix for this card and I get to "cp /downloads/alsa-* ." and it says no directory specified. I am way to new at this stuff to know what to do. Can someone please help walk me through getting this thing working!?

I also found an auto script however it is in French and does me no good, I have no idea what it is saying when I run it.

Thanks

 
Geeve

---

### Post by andru183 on 2010-05-25
hey man, was trying to do sumit else with this card and found this post, the emu 0404, altho now she works sweet and sounds supurb, made me cry blood trying to set it up till i came across this, now it ork just fine but im having troble connecting midi getting it to read, hope it help you man

[http://jg234.co.uk/2010/01/getting-the-e-mu-0404-pci-to-work-in-ubuntu/](http://jg234.co.uk/2010/01/getting-the-e-mu-0404-pci-to-work-in-ubuntu/)

---

