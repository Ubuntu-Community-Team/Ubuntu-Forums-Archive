---
title: "hvr-950 help me this thing is driving me crazy!"
date: 2009-04-21
forum: Mythbuntu
---

### Post by glenn3451 on 2009-04-21
first thing is, im new (very new) to linux. for all intensive purposes lets assume i know nothing from here on out (i dont actually know anything so i can play the role very well)

anywho... onto the topic at hand i have a hvr-950 that i cannot for the life of me get working. my understanding is this, that mercurial had a driver that worked and you had to do extra steps to install it. then v4l came out with a new "tree" (what is this? a compilation of some sort?) that included the driver i needed for this card. i tried many thousands of things on knoppmyth before i gave up and decided it was a good idea to try mybuntu. and go figure i sort of got it to work! i followed the instructions found here -> [http://ubuntuforums.org/showthread.php?t=990185](http://ubuntuforums.org/showthread.php?t=990185)
well i was able to get it working, unfortunatly in the the process i also may have changed a few settings i shouldnt have. so me being man that does not understand linux or the terminal well decided i would reinstall mythbuntu fresh and just do the steps in that thread. well i did it and now instead of having video with no sound i have nothing at all! i guess what i am asking is for alot of help. i really want to use mythbuntu for a home theater pc but at the rate im going i will have to return to windows (at least i am trying linux!!!) if it helps at all i am running...

mobo- MSI K8N Neo4 platinum
psu- Thermaltake 430 watts
graphics card- EVGA nvidia 8600 gts
processor- AMD athlon 3800 x2
memory- ddr 400 OCZ
HDD- 120 gig and 160 gig (right now i have the 160 gig out of the system till i get things set up and running)
cd- Sony DVD-RW

i have no sound card except for whats built into the mobo, and i am using the LAN built in too. if i could just get this set-up running with just this tuner i will work on adding others and a remote at a later time. (also i have the ability to invest some money into new parts for this system but again id like to see it working somewhat first before i go and invest more into it)

any tips/ help on getting things going is greatly appriciated

---

### Post by glenn3451 on 2009-04-24
wow, im alittle disappointed. i expected more help from the community on community based software...

---

### Post by Gerard08 on 2009-04-24
The first thing experienced users are going to ask you is to post your back-end and front-end logs. You also have not indicated which distro and version.  I have just finished a home pc set-up for over-the -air DTV and it was frustrating, but worth it I think.

Have you checked to see whether your tuner is supported?

Look Here:```
[ http://mythtv.org/wiki/Category:Video_capture_cards]("http://http://mythtv.org/wiki/Category:Video_capture_cards")
```

---

### Post by glenn3451 on 2009-04-24
ok, here is what i got...

i have gotten the video to work but no sound. i do have sound on the system because i have played an audio cd on it. i am running jaunty. still cant figure out this sound thing. if someone could leave some insight for me...

---

### Post by glenn3451 on 2009-04-24
oh and i may have forgotten to mention but i dont care about the digital channels just yet. i want to get the analog to work with cable. thanks for any help

---

### Post by Gerard08 on 2009-04-25
> **glenn3451 said:**
> oh and i may have forgotten to mention but i dont care about the digital channels just yet. i want to get the analog to work with cable. thanks for any help

Well, I have had sound issues while trying to get my tuner to work because it receives both over the air analog and digital signals. My tuner does have an onboard sound card but no cable to loop it into my sound-in port of either my mobo or soundin port on my case. Since you are going to use cable, then you probably will process the sound through the same digital signal.

First check:  ```
Sytem-Preferences-Sound-sound preferences--audio conferencing-sound capture. If you have an onboard sound chip on your tuner it should show up here.
```

I would recommend also installing gnome Alsa Mixer from the depos,

You can easily see which is your capture device. There is a small box that says "mute" near the master slide. Make sure that is not checked.

Typing this in the console:
```
aplay -l
```
will tell us more about your sound set-up and ```
lspci -v | grep -i audio
``` will tell us even more about your onboard devices.

Try ```
[http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")
and [http://ubuntuforums.org/showthread.php?t=205449&highlight=C-Media+CMI8738]("http://ubuntuforums.org/showthread.php?t=205449&highlight=C-Media+CMI8738")
```

---

### Post by glenn3451 on 2009-05-06
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and



00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)


no progress thus far. could it possibly be the dev numbers are screwed up? i know the sound on the system works because it can play an audio cd

---

### Post by phroman on 2009-05-06
Ok, do headphones work out of the normal headphone jack on the back of the computer?  The iec958 is your digital audio out, probably SPDIF.  Have you run alsamixer to verify that it is not muted?  Are you using a stereo receiver to play your audio, or some PC speakers or what?  You have to configure mythtv to use a particular audio device.  You can set this from the mythtv front end.  Go to Utilities/Setup > Setup > General > I think the 3rd screen has the audio configs.  Try these settings:  


Audio Output.  try setting this to: ALSA:spdif  
Passthrough output device:  ALSA: iec958
Max Audio Channels:  
Stereo  Upmix:  Passive
Check the box to enable AC3 and DTS to SPDIF

See if this gets you anywhere.

---

