---
title: "[SOLVED] I broke sound on ubuntu and have no clue how to fix"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by AFarris01 on 2008-01-17
Hi...i've got a problem here...when i first installed ubuntu on my machine, i had sound only coming out of the front left speaker of my 5.1 surround sound system.  needless to say this was more than a little annoying, so after some reading and research, i read about this program called PulseAudio that was meant to replace EsounD as the sound server, that supposedly gave better support for surround sound setups.  so i downloaded it from synaptic and it ran fine... then i found the followed the instructions in the Pulseaudio wiki on how to install it, and it worked sort of, but i could only get sound out of the front 2 speakers.  then, i found the wiki for pulseaudio ([https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)) and decided to try followinf the steps it prescribed to get the mixers ans such...so i followed the instructions it gave in the wiki, and thats when the trouble started.  I now have absolutlely no sound from ubuntu at all...nothing from the system, cds, movies, nothing.  i thought maybe that was a problem with the pulseaudio, so i purged pulseaudio and reinstalled esound, but i still have no sound.  finally i got desperate and reinstalled pulseaudio according to the wiki as a last effort to regain my sound after trying numerous other things, and i noticed something while i was fiddling with the sound manager.  it has a volume meter, a mixer, and a test sound bank, and when i try to test play any sounds, run a cd, or play a game/movie the sound server shows a mono sound channel having been created, and the volume meter shows actvity, but i get no sound out of my speakers at all.  

thats my story, here are some relevent command line outputs...
----------------------------------
andrew@BEC-LIN:~$ asoundconf list
Names of available sound cards:
CA0106
----------------------------------
alsamixer only has one bar in it, and its called 'pulseaudio', its at 100% and unmuted, so i didnt see the point of uploading a screenshot of it, but if someone wants me to, i will happily do so
---------------------------------
andrew@BEC-LIN:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
--------------------------------------
andrew@BEC-LIN:~$ lspci -v
01:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>
***I cut out all the things i didnt figure would have to do with the sound card (ethernet card, graphics, etc...) but again, if someone would like, ill post the whole output***
---------------------------------------
thats all i can think of...does anybody have any ideas?  :confused::confused::confused:

---

