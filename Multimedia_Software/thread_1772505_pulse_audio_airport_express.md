---
title: "pulse audio airport express"
date: 2011-05-31
forum: Multimedia Software
---

### Post by svenole on 2011-05-31
I'm running 11.04 pulse audio for streaming music to my airport express boxes. This seems to work, but it messes up access to airport express devices from my mac,ipad,iphone devices. If I choose to stream sound to an airport express, it locks down that device from all other devices until you actually disconnect the ubuntu device from the network or disable airport express discovery in the pulse audio preferences. Expected behaviour should be to release the airport express box when connecting to another device (ex. internal speaker), but this does not happen.  Any clues on how to fix this would be appriciated. As of now this software can not be used for streaming music to airport express devices in a mixed environment.

---

### Post by ar7 on 2011-06-01
Very interesting to hear that you got it working in the first place -- I've been trying to do that over the last few days with no success. I've read all the information online that I could, but it's still not working. Your post is is he only recent example of someone getting it to work :-O

Are you using one of the new Airport Express devices? Could you perhaps explain a bit more what steps you took, and what versions you're using? Would really appreciate that!

As for your issue, I did read some forum post where the guy was complaining about the opposite happening i.e. iTunes locking the Airport Express and then he couldn't use pulseaudio alongside.

---

### Post by mobodo on 2011-06-04
I have a similar problem, except I don't even have to select the Airport speakers in pulse audio to lock Airplay.  When I boot ubuntu or reboot the Airport device, ubuntu locks the device and it becomes unusable to anybody else.  I have to disconnect my ubuntu box from airport, reboot the airport device and then it's unlocked.

Pretty annoying considering it's not even selected as the output device in Pulse Audio.

Fortunately, I don't reboot either devices very often.  If I find a solution, I'll post it here.

Happens since I upgraded to 11.04

---

### Post by gfunkdave on 2011-06-16
> **mobodo said:**
> I have a similar problem, except I don't even have to select the Airport speakers in pulse audio to lock Airplay.  When I boot ubuntu or reboot the Airport device, ubuntu locks the device and it becomes unusable to anybody else.  I have to disconnect my ubuntu box from airport, reboot the airport device and then it's unlocked.

Pretty annoying considering it's not even selected as the output device in Pulse Audio.

Fortunately, I don't reboot either devices very often.  If I find a solution, I'll post it here.

Happens since I upgraded to 11.04

The same thing happens to me. I have the checkbox for "Make discoverable Apple airtunes devices available locally" unchecked, but Ubuntu still locks my Airport Express.

---

