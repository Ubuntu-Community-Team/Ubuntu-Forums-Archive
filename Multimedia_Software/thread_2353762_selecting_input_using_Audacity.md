---
title: "selecting input using Audacity"
date: 2017-02-24
forum: Multimedia Software
---

### Post by pete1977x on 2017-02-24
I am new to Audacity. I will be recording via the USB in on my PC from a Behringer UCA222 converter, the little red box.  I downloaded Audacity and went into preferences.
The input for recording/devices is set to CD:0 or something like that. Is Audacity going to pick up the data coming into the program from the USB port??? There was no option that said exactly USB
on the drop down list. There wont be any other stuff connected to the other ports when I record.I have a CD tray but it wont be involved.
also what kind of recording levels are about right ????I will be recording from some older tapes....the source tapes are digital then analog then back to digital via USB into Audacity.

---

### Post by Autodave on 2017-02-25
Audacity should find it w/o a problem: just have the USB cable connected and the Behringer running *before* you load Audacity. You will then see a few new options listed in the *INPUTS *area. Normally, the first new one is the one you need / want.

As far as the volume, since it will be coming into the PC as a digital signal, you will not be able to adjust the volume in Audacity while you are recording. You need, if possible, to adjust the level of the signal *leaving *the Behringer. However, do NOT have the signal too loud to where clipping will occur: your recording will sound badly. Better to record, then go into *EFFECT *and maximize the level of the recording.

---

### Post by Bucky Ball on 2017-02-25
> **Autodave said:**
> However, do NOT have the signal too loud to where clipping will occur: your recording will sound badly. Better to record, then go into *EFFECT *and maximize the level of the recording.

Better to get a good level that isn't peaking in the red before you start recording then normalise or 'Effects> Amplify' after recording if required. If using 'Amplify' it will suggest a suitable +dB to get your original recording to somewhere close to 0dB. ;) 

Play the loudest you're going to play during audition and adjust the recording level so it's not peaking, then hit 'record'.

If your USB device is not showing in the 'Inputs' drop down list, open a terminal and give us the output of this command, between code tags please. 

```
lsusb
```

---

