---
title: "Line-in to Digital-out (SP/DIF)"
date: 2009-03-21
forum: Multimedia Software
---

### Post by alex2399 on 2009-03-21
Problem:
I have a TV card (BT878 ) from hauppage, that has an analog line out, connected to the analog line-in of my onboard soundchip (Realtek ALC889A). I use the digital SP/DIF out from my onboard soundchip to transfer sound to my DCC player that functions as a DAC.

When playing music on the computer, its output is routed in stereo channels to the SP/DIF at 44,1 kHz. This works, everything I play gets its output to the SP/DIF. Except the sound via line-in. So the problem might be that its not being digitized, or not routed in the right way. Sound from the line-in is however played on the analog outputs of the onboard soundchip.

So:

```
TV card      Onboard     Onboard
line-out---->Line-in---->Line-out--------->works
(BT878)      (ALC889A)   (ALC889A)
                 |
                 |
                 v
             Onboard       
             SP/DIF out--->no output
             (ALC889A)
```

It's not that the DCC-900 cannot read the signal, since it stays at 44,1kHz, so nothing changes with SP/DIF output characteristics. I can also play music through it when having sound from the TV card via analog out.

I tried alot of mixers(PA,ALSA mixers), but nowhere is there some routing table of sound regarding this, or where it stops.

So the question:
How do I diagnose the problem and how do I make it work so the sound from the analog line-in is digitized in real-time or routed correctly for output to my DCC-900?

---

### Post by alex2399 on 2009-04-02
Bump....

---

### Post by alex2399 on 2009-04-22
And up...

---

### Post by kengyu on 2009-08-07
> **alex2399 said:**
> Problem:
I have a TV card (BT878 ) from hauppage, that has an analog line out, connected to the analog line-in of my onboard soundchip (Realtek ALC889A). I use the digital SP/DIF out from my onboard soundchip to transfer sound to my DCC player that functions as a DAC.

When playing music on the computer, its output is routed in stereo channels to the SP/DIF at 44,1 kHz. This works, everything I play gets its output to the SP/DIF. Except the sound via line-in. So the problem might be that its not being digitized, or not routed in the right way. Sound from the line-in is however played on the analog outputs of the onboard soundchip.



I have the same problem with an Avermedia TV Capture 98 ( BT878 ) and the integrated soundcard in a Gigabyte motherboard ( ALC889A ).

---

### Post by l3iggs on 2009-08-07
same issue here. however, i have something useful to add. try going to System-->Sound and clicking the test button next to Sound capture. For me, (w/a Zotac ION MoBo and Alsa v1.0.18 ) that causes the analog line-in to be passed through to my digital out. I also had to turn up the "capture" volume (recommend 0 dB) and set capture source to "line" in $ alsamixer

---

### Post by l3iggs on 2009-08-09
figured it out! yessss!!

first use alsamixer to configure capture from 'line' and enable your digital output

then run:
```
arecord -f dat | aplay
```
this essentially 'records' your line input and pipes that directly to your output
you'll get your analog line input coming out of your digital output in 2 channel @ 48,000 Hz

i'm sure there is a better way to do this (it eats 2-3% of one of my CPUs :(). if someone knows it, by all means please post here

i have the above code run on login so that my line input always plays on my digital output

---

### Post by markbuntu on 2009-08-10
You should check with the alsa devs since that should be handled by the alsa hardware driver since it is internal switching in the card or should be.

---

