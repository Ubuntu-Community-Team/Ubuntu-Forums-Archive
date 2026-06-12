---
title: "Feisty64 / P5B Deluxe , SoundMax Mic not recording"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by Ancient1 on 2007-07-12
* P5B Deluxe , SoundSux ( NOT a mistake)
* HDA Intel / Alsa Mixer
* Feisty AMD64, latest everything .. just installed a week ago

No Mic Recording , even though the mic IS working i.e I can hear the mic ,  
The mic[COLOR="Red"] IS working [/COLOR]with EKIGA !  however, when testing , its reverberating , albiet fainter and fainter. 

Alsa Mixer , and every mixer I tried, doesn't show MIC in recording , only Capture - select device . and Capture 1 & 2 ..  

Tried alsa conf setting mentioned in the documentation and on the net . i.e HDA Intel - define different types 
Tried Alsa project's guide [http://alsa.opensrc.org/Hda](http://alsa.opensrc.org/Hda)  and similar 

[COLOR="Blue"]There is an issue , in Windows XP too , with this SoundSux when enabling front mic , shuts down the backpanel mic . 
Obviusly the mic , and mic boost are working . but the linking to Record isn't working[/COLOR]

^&%*$^#

---

### Post by drplix on 2007-07-12
Same problem here.  Feisty 64 on HP 6715b laptop with SoundMax AD 1981 chip.  Plays sound fine but cannot record any souds and I don't see mic in any mixer.  Have installed latest alsa 1.14RC4.  Still no mic.

Please help someone - I use skype for business calls everyday.

PS Audio is all working fine when I reboot and test it on Vista  - but I couldn't stand using Vista for more than 5 minutes.

---

### Post by drplix on 2007-07-15
I found a cure to this...

To get the SoundMax / Azalia card to work use this howto:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Note you must use the latest 1.0.14 alsa archives (not RC14 as mentioned in the howto)

Next do the following to get a consistent boot.

1) sudo alsaconf and select "SB600 Azalia"
2) Delete /etc/modprobe.d/alsa-base (alsaconf installs /etc/modprobe.d/sound which seems to be all you need)

Reboot.

Lo and behold. Surround sound options and working recording. I used audacity to test.

---

### Post by Ancient1 on 2007-07-16
well , I already did that guide , albeit with 1.14RC4 , so I simply re-did with 1.14 final .   
( should I have uninstalled the earlier version ? how )   

I did run alsaconf and it was the same  "Intel Corporation 82801H (ICH8 Family..)" = Intel-HDA 
I renamed alsa-base to alsa-base.old  , rebooted .  
( should I have done Make Clean ? ) 

Beside a new "Digital" recording option , nothing changed .  I than tried rebooting with alsa-base 
Sound Recorder still doesn't record. :( 

So the bottom line is No, the new alsa version doesn't solve the problem.  

I am going to try to reinstall the sound recorder , as the mic worked before in Ekiga

---

### Post by Podmornik on 2007-09-17
I have the same problem with my HP 6715b laptop and it seems that I can't fint the solution for it. I even upgraded Feisty to Gutsy but the problem remains. Did anyone find the solution?

---

### Post by drplix on 2007-09-17
I have the same machine.  I got it working by compiling my own Alsa (see comment above). I was hoping that Gutsy would solve this - am still on Feisty.

There's a topic with general pointers on setting up the HP 6715b here:

[http://ubuntuforums.org/showthread.php?t=488406](http://ubuntuforums.org/showthread.php?t=488406)

---

### Post by Podmornik on 2007-09-17
OK, I'll try this method in the afternoon and we'll see. Thank you!

---

