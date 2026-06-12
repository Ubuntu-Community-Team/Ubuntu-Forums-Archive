---
title: "Sound card Problem"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by glos_wifi on 2007-04-18
Let me start this off first by saying i am completly new to Linux and would really appreciate any help you peeps can provide.

Ok now onto the problem.

Three days ago i installed Ubuntu 6.10 and i have no sound. Ive checked that its set to the ALSA Mixer setting and that they're all unmuted. I also tried installing a new version of ALSA but that kept crashing the system on reboot and when i managed to get into the desktop the system would not pick up any sound devices.

From what i have managed to work out the audio device is a Sigmatel STAC 9200 (Onboard Audio in a Gateway MX3311b).
Thanks in advance for any help.


P.s. - As a side note i recently had to wipe this laptop and installed it duel boot with XP, this also had a problem with the Audio and i had to trek around the internet for the driver, and as a result i now have a copy of the audio driver. I was wondering if there is a way to use this driver in linux at all.

---

### Post by glos_wifi on 2007-04-19
**Update**

Did a fresh install of Ubuntu Feisty 7.04  today.

I had my headphones in the socket and noticed the headphone buzz . . . up until Ubuntu started to load that is.


Any ideas?

---

### Post by glos_wifi on 2007-04-22
*Bump*

Please help, even a message saying no would do (not preffered mind).

---

### Post by Dave54 on 2007-05-01
So you have no sound in ubuntu? Try this:

1. First Double-click the sound icon
2. click Edit > Preferences
3. check every box
4. close that, and raise every bar to max
5. note there are many tabs. go to each and fiddle with options
6. click Change Device > (next device on the list)
7. Repeat steps 2 through 7 for each device.

Next go to System > Preferences > Sound
Next to the "test" boxes, select each device and test each and every one.

I had no sound, but after this I realized that "Master" did nothing and my sound depended on "headphone" and "PCM".

Good luck.

---

### Post by glos_wifi on 2007-05-03
Ive just done all Dave54 and it doesnt work still :( 

After looking on the internet im noticing that this is likely to never get working, since it is a NVidia varient the more i look around.

The dreaded MCP51 HDA :S

---

### Post by tentwelveeight on 2007-05-03
I had NO sound out of my Intel 82801db-ich4 sound card. I did everything the guy above said to do and it still didn't work UNTIL I UNCHECKED "external amplifier". Now I'm groovy baby! YEAH!

---

### Post by glos_wifi on 2007-05-04
Where would the "External Amplifier" box be? Im sorry if thats a stupid question, but im a noob at this.

---

### Post by felicity on 2007-05-04
glos_wifi: I think the option for External Amplifier only exists if you have something like that connected to your system.

Dave54: Thanks for the info! My sound has been a bit scratchy at times in Feisty but it seems to be working better now that I changed the settings in the Devices section of the Sound Preferences.

---

