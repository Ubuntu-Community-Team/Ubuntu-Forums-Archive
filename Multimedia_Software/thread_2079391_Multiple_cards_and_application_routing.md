---
title: "Multiple cards and application routing"
date: 2012-11-01
forum: Multimedia Software
---

### Post by not4us on 2012-11-01
Hope someone can help me out here.
I am trying to move over to Ubuntu fro my podcast recording .
Currently in windows I use Audacity and Skype and want to replicate that on Linux.
I have 2 dedicated USB sound interface (Behringer UCA222) connecte to an 8channel mixing board.
In Windows I have it set so that Skype uses one of the USB interfaces that has the input and output connected to the mixer.
Then the mixer sends the output to the second USB interface which is set as the recording device in Audacity.
All along the internal sundcard (Realtek) is used as the default sound device for the whole system.
So, in other words, what I need to do is:
[LIST=1]
[*]Skype use USB card 1
[*]Audacity use USB card 2
[*]System uses internal card
[/LIST]
I have tried to get this working on PulseAudio but can't figure how to "link" apps to devices.
Or should I be using Jack for this? I know Skype doesn't work with Jack but I thought I could route Pulseaudio to Jack to solve this. Tried but failed :(

---

