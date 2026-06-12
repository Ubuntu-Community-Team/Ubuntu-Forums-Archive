---
title: "[SOLVED] No MIDI on Sound Blaster Platinum (Live!)"
date: 2009-01-18
forum: Multimedia Software
---

### Post by celafon on 2009-01-18
Hi,

I have not used midi since 6.4 or something like this. It was working just fine and I could load sf2 files and hear them OK (with sfxload tool).

Currently I am on 8.10 and tried to load a midi file, but it appears there's no sound... I can see the midi ports:

bartek@ubik:~$ amidi -l
Dir Device    Name
IO  hw:0,0    EMU10K1 MPU-401 (UART)
IO  hw:0,1    Emu10k1 Synth MIDI (16 subdevices)
IO  hw:0,2    Emu10k1 Synth MIDI (16 subdevices)

but when trying to play a file - it won't sound.


OK... edit (while posting):

I have just tried to sfxload another sound font file... It did work. Now the question is: why the heck it is not working by default? I've spent like a day trying to run this thing... Now it looks that I forgot only about this stupid command... It would be cool if this thing would have been run for the user once we have a sound card that requires loading a sound font - or at least offered as an option (I am sure there is a free/open sound font).

---

