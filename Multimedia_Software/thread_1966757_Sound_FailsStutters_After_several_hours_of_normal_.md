---
title: "Sound Fails/Stutters After several hours of normal playing"
date: 2012-04-27
forum: Multimedia Software
---

### Post by CheeseRoller on 2012-04-27
I have a software program that uses SDL mixer to play wav files. The OS is the latest version lubuntu and is using the alsa sound device.

The program is required to run for long periods of time for automated testing purposes, the program can be left running continuously for 3-4 days.

I start the automated test and the program runs through all its features in a loop and the sound is working correctly.

When I come to look at the program the next day the sound has gone wrong. Instead of tunes and sound effects, all I can hear is a stuttering type of noise that occasionally changes pitch, and occasionally no audio appears to be active as the speakers are silent.

The rest of the program is still running correctly and doing all of the things I expect it to do but the audio is not working as intended.

Has anyone encountered this kind of problem with ubuntu/lubuntu before?

---

### Post by marinara on 2012-04-27
I have a similar problem when I put my pc into suspend, usually i get a full blast of sound when I wake it up.  But I haven't had that problem, no.

---

### Post by serapch on 2012-04-28
Do you check the alsamixer to view the speaker levels, because I had the same issue with no sound through speakers.

---

### Post by CheeseRoller on 2012-04-29
I realised last night that the o/s is not the latest version. I had assumed it was as I did not do the install, but it's actually 10.10

---

