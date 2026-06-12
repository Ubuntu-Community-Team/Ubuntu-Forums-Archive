---
title: "Audio doesnt work"
date: 2014-02-07
forum: Multimedia Software
---

### Post by daniel109 on 2014-02-07
So my audio works on bootup and i can see that under sound settings when i play audio it does recognise there is music playing but there isnt actually any sound ; also headphones do work .

thanks for any advice

thanks for any help

---

### Post by tgalati4 on 2014-02-07
Open a terminal and post the output of:

```
aplay -l
```

That's a lower case L.  If you plug and plug your headphones several times do you get any sound?  Sometimes a switch in the headphone jack can be faulty.

---

### Post by daniel109 on 2014-02-07
> **tgalati4 said:**
> Open a terminal and post the output of:

```
aplay -l
```

That's a lower case L.  If you plug and plug your headphones several times do you get any sound?  Sometimes a switch in the headphone jack can be faulty.

i got this :

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and i tried the headphones a couple of times , no difference .

---

### Post by tgalati4 on 2014-02-07
Run speaker-test:

```
man speaker-test
speaker-test
```

---

### Post by daniel109 on 2014-02-07
> **tgalati4 said:**
> Run speaker-test:

```
man speaker-test
speaker-test
```

I got this now 

```
NAME
       speaker-test - command-line speaker test tone generator for ALSA

SYNOPSIS
       speaker-test [-options]

DESCRIPTION
       speaker-test  generates a tone that can be used to test the speakers of
       a computer.

       speaker-test by default will test the default device. If  you  want  to
       test  another  sound device you will have first to get a list of all of
       the sound cards in your system and the devices  associated  with  those
       cards.  Notice  that  there might be for example, one device for analog
       sound, one for digital sound and one for HDMI sound.  To get  the  list
       of available cards and devices you can run aplay -L.

       $ aplay -L
       null
           Discard all samples (playback) or generate zero samples (capture)
       default:CARD=ICH5
log file: peaker-test

```

and thanks for helping

---

### Post by tgalati4 on 2014-02-07
The manual page will give you all of the switches to try.  Use the spacebar to page forward and "q" to quit.  Let us know if you get any sound.

This page is a little detailed, but take your time and see what works for you.  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

