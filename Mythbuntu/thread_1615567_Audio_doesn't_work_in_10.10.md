---
title: "Audio doesn't work in 10.10"
date: 2010-11-07
forum: Mythbuntu
---

### Post by Sum Guy on 2010-11-07
My new Mythbuntu media setup currently has no sound. I've looked around, and found suggestions to check muting in alsamixer. I tried to do this, but there was no alsamixer installed, either in the applications menu or the terminal. I tried installing the Alsamixergui, but it only lets me select the integrated sound card. Any ideas? Thanks.

---

### Post by nickrout on 2010-11-07
> **Sum Guy said:**
> My new Mythbuntu media setup currently has no sound. I've looked around, and found suggestions to check muting in alsamixer. I tried to do this, but there was no alsamixer installed, either in the applications menu or the terminal. I tried installing the Alsamixergui, but it only lets me select the integrated sound card. Any ideas? Thanks.

your post implies you have two sound cards but does not tell us what they are. 

alsamixer runs in a terminal. type alsamixer and then you can use the F6 button to select other sound cards.

Also you need to set up the correct sound device in the frontend setup - I cannot recall which screen, general I think.

---

### Post by Sum Guy on 2010-11-08
Thanks for the suggestion on alsamixer, I had originally assumed (incorrectly) that it would run in the terminal emulator in xfce. The computer has an integrated sound card on the motherboard, and a PCI sound card, shown in alsamixer as follows:
Card 0: Intel ICH5
Card 1: {not a sound card}
Card 2: SB Live! Value [CT4832]
Trying ALSA:default yields sound from the motherboard chip, but not the PCI card. I wish to set the front end to use the stereo analog Line Out, with volume control in MythTV. The SB Live! sound card has the following connectors on the back, if it is using standard connectors:
Digital Out
Stereo Line In
Microphone
Line Out
Rear surround sound speakers
...and a Joystick port. All connectors other than the joystick port are 3.5mm.

Thanks for helping me so far.

---

### Post by bance on 2010-11-08
Try adding your card in front-end set-up:-

```
Alsa:default:CARD=2
```

good luck Steve,

---

### Post by Sum Guy on 2010-11-08
Great, it worked! Thanks to both posters for the help, you made this quick and painless to fix.

---

