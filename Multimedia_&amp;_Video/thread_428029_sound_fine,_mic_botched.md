---
title: "sound fine, mic botched"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Flac on 2007-04-29
Alright... I know there are 50 billion microphone threads. I've read most all of them, of the ones i read, none of them helped me. Its quite possible that Theres no solution to be found for me. I understand that. On the off chance that somebody knows something though... Heres my issue

im running an xubuntu fiesty install. Sound card is a creative soundblaster Audigy LS.

I have sound, thats not an issue. Problem is that my headphones mic isnt working. I've tested it on my room mates windows machine and it works, i know its not the microphone itself.

Details about my problem are thus. If i crank all the volume up, and set "captur" on "mic in" in the term based alsamixer, i can hear the microphone buzzing, if i tap it i can here the microphone pick up the tap, but when i run any application such as skype or teamspeak, there is nothing.. Further more, if i load a graphical mixer, such as "xfce4-mixer" or "alsamixergui" the sliders for mic are forced into the off position, i cant touch them. I have no option for "mic boost" anywhere which has been a solution in a few other threads.

 Im pretty much at my wits end, so if anyone has any idea's at all, i'll try anything short of rubbing honey on my thigh's and dancing like a chicken.

---

### Post by kafkaian on 2007-05-01
Ditto. I've given up using my headset mic, or any mic for that matter

---

### Post by ka9qlq on 2007-05-08
This mat or may not work BUUUUTT

Microphone not working (Sporadic using Skype and Ekiga) and general audio problems
 
18. Microphone not working
 
On my system, I could get the microphone to work by simply un-muting the correct channels using alsamixer. To do this, open the ALSA mixer GUI form a terminal alsamixer the ALSA Mixer GUI will be displayed
 
Now make sure all outputs are un-muted. Scroll through the outputs using the LEFT and RIGHT arrow keys, and press M to un-mute a channel (muted channels show an MM symbol). Use the UP and DOWN arrow keys to raise and lower the volume for each channel. Press TAB to switch to capture settings. Select Mic and press SPACE to enable the microphone. Now enable microphone capture my selecting Capture, and pressing SPACE. Depending on your microphone, you may need to enable MIC boost to get some extra umph from your sound input.
 
The volume of the input channels depends on your microphone. These settings worked best for me on a desktop microphone:
MIC: 71 MIC Boost: 33 Capture: 73
 
Now test the microphone by going to Applications - Sound & Video - Sound Recorder and select "Capture" in the "Record from input" field. On my system, mixing worked too - meaning I could play games whilst talking on Skype.
 
After following the above steps, your microphone may still not work, which appears to be linked to the a missing file /etc/asound.names. Executing
 
sudo alsactl names  sudo alsactl store 
 
to generate /etc/asound.names and /var/lib/alsa/asound.state seems to fix sound problems.

---

