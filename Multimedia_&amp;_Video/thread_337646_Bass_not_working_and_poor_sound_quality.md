---
title: "Bass not working and poor sound quality"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by dustoashes on 2007-01-13
Hi,
I have a Nvidia nForce2 on my Abit nf7-s mobo. I have read through many pages of threads but I haven't found a solution to my problem:

1. the bass does not work. I've enabled surround and "duplicate front" and it still doesn't work. Other speakers work fine.

2. the sound quality is rather raw, crunchy. 

I use Ubuntu 6.10. I'd appreciate it a lot if someone explained if i need to install nforce drivers or just do some other trick to improve these things.

---

### Post by dustoashes on 2007-01-13
No one? :(

I've tried both [this]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_the_ALSA_drivers_from_a_.2Afresh.2A_kernel") and [this]("http://ubuntuforums.org/showthread.php?p=2008044#post2008044"). My speakers are working minus the subwoofer. My sound card is also recognized.

---

### Post by Stochastic on 2007-01-13
Well I'd like to give you some advice but you've listed your motherboard model not your soudcard model.  Do you know what the soundcard is?  I assume that if you've listed your motherboard then the souncard is an onboard one?

Look in System>Administration>Device Manager and find anything that talks about sound if you're lost.

---

### Post by dustoashes on 2007-01-13
I know what a soundcard is. 

[My motherboard]("http://www.abit-usa.com/products/mb/techspec.php?categories=1&model=6")

> 
6-Channel AC 97 CODEC on board
- Professional digital audio interface supports S/PDIF Out
- NVIDIA SoundStorm with real-time Dolby Digital 5.1 encoder

---

### Post by Stochastic on 2007-01-13
I didn't mean to be condecending or below your knowedge level but you hadn't posted any info about your soundcard and you have only a couple posts on this forum so I wasn't about to assume anything about what you did or didn't know.

What does the soundcard show up as in the Device Manager?
What levels are in the alsamixer when run from the terminal?

---

### Post by dustoashes on 2007-01-13
Don't worry, I didn't mean to sound insulted ;) 

Anyway, I've added screenshots from alsamixer and Device Manager. Hope it helps. Thanks :)

---

### Post by Stochastic on 2007-01-13
what types of outputs does your soundcard have?
where are your speakers hooked into from those outputs?
when you say it sounds crunchy, how crunchy?

---

### Post by dustoashes on 2007-01-13
The soundcard has 5.1 output, connected to my speaker system. They work fine in WIndows (nforce2 drivers, surround wizard). 

I don't know how crunchy.. like the sound is coming from speakers that do not use no smooth equalizing? I dunno... maybe the experience without the subwoofer just makes it sound worse.

---

### Post by Stochastic on 2007-01-13
I mean is there one cord attached to your soundcard or 6 or 3?

---

### Post by dustoashes on 2007-01-14
> **Stochastic said:**
> I mean is there one cord attached to your soundcard or 6 or 3?

Yes, the cords from my soundsystem are attached. There's four of them attached... and there's one more (output i guess?) that's free of cords.

---

### Post by Stochastic on 2007-01-15
Where do these cords run to?  What are the outputs on the soundcard labled as? It seems very strange that you have four cords for a 5.1 surround system (a six channel system).  Which cord has the subwoofer and where is that cord plugged into?

---

### Post by stuh84 on 2007-01-15
Having four cords doesn't seem strange at all. Given that two will carry stereo, and two will be mono, thats 6 channels, lo and behold, 5.1

---

### Post by dustoashes on 2007-01-16
Hey there,
well I didn't even try to re-arrange the cords. So I plugged them a bit differently and the subwoofer works fine now. However this is highly inconvenient since I still have XP and the arrangement of the cords works differently there (as it was before). What do ya think?

---

### Post by Stochastic on 2007-01-18
> **stuh84 said:**
> Having four cords doesn't seem strange at all. Given that two will carry stereo, and two will be mono, thats 6 channels, lo and behold, 5.1

I guess that would work, just didn't think that they'd do only some stereo and some mono.  Why would they bother with four if three stereo would work just as well?

> So I plugged them a bit differently and the subwoofer works fine now. 

What did you change to get it to work? (just in case anyone else with that same card has the same troubles or incase it's something that will lead to a fix without swapping wires)

---

### Post by dustoashes on 2007-01-18
> **Stochastic said:**
> What did you change to get it to work? (just in case anyone else with that same card has the same troubles or incase it's something that will lead to a fix without swapping wires)

I simply re-arranged the cords a little. Just do a little experimenting until the woofer can be heard and the sound comes from other channels as well. 
In the volume controls the Master is 100%, Surround as well... and PCM is somewhat above the middle.

---

### Post by stuh84 on 2007-01-18
In terms of why use 4 cables, its more a standards thing really. The left and right channels are in stereo to each other, so can be used like a stereo feed. The rear channels also are corresponding to stereo, albeit rear stereo. Centre and subwoofer do not correspond to any sort of relative position, with centre going in the centre, and sub going anywhere in the room. 

The idea is, that the centre channel could be the exact opposite side of the room to the sub, whereas the two fronts and two rears have to at least be in the same relative position to each other.

---

### Post by Stochastic on 2007-01-21
I guess that makes sense, my experience is mostly in quadrophonic and octohponic surround situations where there is no centre channel but rather an even circular surround of the listener.  I find these setups to give a much better aural image - just personal preference.

---

### Post by dustoashes on 2007-01-23
What could I do to surpass the rearrangement of the cords each time? As I mentioned, the settings in WIn XP take a different cord arrangement from Ubuntu.

---

### Post by Icarosaurus on 2007-03-12
I have similar issues:
[http://www.ubuntuforums.org/showpost.php?p=2015788&postcount=95](http://www.ubuntuforums.org/showpost.php?p=2015788&postcount=95)

---

### Post by Berylfun on 2007-03-13
I experience the same problem having the same chipset (nforce2) in my MSI motherboard. The only thing that i didn't try was this. Tomorrow i'll give it a try and hopefully it will make some noice to come out from my sub.

---

