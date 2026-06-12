---
title: "Problem with sound in new desktop"
date: 2011-06-23
forum: Multimedia Software
---

### Post by gylti on 2011-06-23
Hi I have a new comp and I have installed Ubuntu 10:10 on it. I like to listen to music and play Runescape a java online game. I can't play any music at all and can't get sound effects in Runescape But CAN get the music of the game online. I have unmuted everything in GNOME Alsa and am using a good headset that works fine with my other computer. 

The mb is M4A78LT-M and Im getting 2 sound cards in Sound Preferences, the onboard and RS780 Azalia controller (HDMI) Stereo 
In Alsa it says I have 2 sound cards VIA VT1708S and ATI RS690/780 HDMI and I have 2 tabs but the tab for the ATI one is empty, no sliders or anything to configure.
 
          in terminal I put in aplay -l
 

 **** List of PLAYBACK Hardware Devices ****  
 card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]  
   Subdevices: 2/2  
   Subdevice #0: subdevice #0  
   Subdevice #1: subdevice #1  
 card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 
Can anyone advise me how to get the sound right please?

---

### Post by gylti on 2011-06-23
I found the Asus motherboard support on the asus site and dl and followed their instructions. Just concentrated on reinstalling the sound Thought I'd broke it then just decided to use the onboard sound and rebooted, the headset kicked in after i set the sound preferences and unmuted in GNOME Alsa again .. Just happened to have Uprising by Muse running to test sound :))))  WOW!I may be shouting for a week till my ears adjust.. No idea what it was that worked but generally thats what I did if it's any use to anyone.

---

