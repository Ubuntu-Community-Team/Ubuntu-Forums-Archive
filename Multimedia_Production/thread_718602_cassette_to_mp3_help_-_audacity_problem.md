---
title: "cassette to mp3 help - audacity problem"
date: 2008-03-08
forum: Multimedia Production
---

### Post by elj4176 on 2008-03-08
I have an old cassette tape that I want to transfer to wav and then to mp3. I thouught Audacity would do the trick but i'm having trouble with it.
Cassette player headphone out  --> laptop microphone in --> audacity

it starts recording fine until about 30 seconds in to the recording the levels drop to almost silent. If I try to adjust them by turning up the cassette player volume I get a ton of distortion. If I turn up the mic levels on the laptop I get no difference in the levels.

any help would be appreciated. This was using audacity in windows xp because I couldn't get anything to record using the linux version. I know it has to do with my HP laptops goofy hardware and the alsa settings but I cannot figure it out. thanks!

---

### Post by toobuntu on 2008-04-25
mismatched impedance: headphone out is a line level out measured in volts, mic in is _not_ a line-in and is measured in millivolts.  you may be burning out the mic input and that's why it gives out on you.

i have a device that is a cassette deck with a USB out and it works fine. but when i tried doing what you are doing, i would get a lot of artefacts, distortion and clipping.

---

### Post by toobuntu on 2008-04-25
mismatched impedance: headphone out is a line level out measured in volts, mic in is _not_ a line-in and is measured in millivolts.  you may be burning out the mic input and that's why it gives out on you.

i have a device that is a cassette deck with a USB out and it works fine (ION tape2pc). but when i tried doing what you are doing, i would get a lot of artefacts, distortion and clipping.

---

