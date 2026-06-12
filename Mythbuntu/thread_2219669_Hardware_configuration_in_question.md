---
title: "Hardware configuration in question"
date: 2014-04-25
forum: Mythbuntu
---

### Post by seth10 on 2014-04-25
I would like to know if these parts would make a decent MythTV system.  I am unsure if it would even work so I am hesitant to buy. I have attached a picture of my list.

---

### Post by seth10 on 2014-04-25
Anybody?

---

### Post by blm-ubunet on 2014-04-26
The HD4600 is about equal to nVidia GT610.
The intel GPU in SNA & Ivybridge are still lame.

If you are playing back broadcast (interlaced) TV I would think that is the above is the (absolute) bare minimum.
But a good CPU can still deliver okay performance.

Note the FOSS radeon driver supports VDPAU (interlacing is still not perfect AFAIK), so cheap AMD h/w is an option.
Nothing touches Intel for power efficiency.

---

### Post by seth10 on 2014-04-26
So you're saying that it would be better to increase the CPU power? Would an i7 of beefier specs work?

---

### Post by khPWXxF on 2014-04-26
1.  Is that an amd graphics interface?  Linux AMD driver support is generally thought to be inferior to Nvidia (best) and Intel.
2.  Why the firewire ports?
3.  What signal are you hoping to capture?  What will capture it?
4.  2GB is workable but a bit low, especially if you need to allocate some to a graphics card.
Phil

---

### Post by seth10 on 2014-04-26
It is an intel chip.  The FireWire is for direct capture of digital cable right from the stb.

---

### Post by blm-ubunet on 2014-04-26
There is almost no long term prospect of recording via firewire from STB in US (afaik).
The analogue hole (macrovision?) or cablecard tuner (not the copy once!) are your options.

---

### Post by seth10 on 2014-04-26
Alright. Thank you.

---

### Post by drink1297 on 2014-05-02
Is this for a frontend or backend, or combo?  If it is for a frontend, why not a blu-ray player, that is what I did, so I have my myth frontend and blu-ray all in one...I also bought a sysboard with an onboard HDMI and plug that right into my surround sound.
Proc wise, I usually use an AMD sempron...dirt cheap and work great, there is not much processing going on in the frontend, and depending on the capture cards, usually not much in the backend.

My personal opinion...Backend should have a large harddrive, and the frontend should pack all the toys for you viewing pleasure.

---

### Post by seth10 on 2014-05-02
My hopes were for a combo system that I could pack into a small form factor and keep under the STB. I want just enough to record HD digital cable. I've read somewhere that you can capture the digital signal directly from FireWire already encoded as MP4. My STB definitely has a FireWire port on the back so I don't really see the problem with using FireWire.

---

### Post by drink1297 on 2014-05-02
You can use an HDHomerun Prime, that has 3 capture points for about $100....that will allow you use of PiP on the system, as well as watching one show while recording another.  You have to understand that with the system, if your recording (via firewire or not, and I don't know about the fire wire recording bit) your using a capture point, so you can only watch what is being recorded.

You need to have a capture point for each 'session' or monitor watching (including if you use Picture in Picture feature).  If your not interested in any of the features, and simply want to record, you probably really don't want to even mess with MythTV, however if you do wonder into the frey, I think you would be most amazed at just how much the system can do, which I think is why you will find most pushing capture cards with multiple interfaces, once you have it set up, I think you will end up doing more than recording with it.

---

