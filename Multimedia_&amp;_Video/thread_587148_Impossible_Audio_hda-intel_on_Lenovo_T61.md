---
title: "Impossible Audio: hda-intel on Lenovo T61"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by walrus1024 on 2007-10-22
I've tried every tutorial / how to that I can find about getting audio to work on the Lenovo T61 which is using an hda-intel.

I made sure the modem is enabled in the bios, after trying unsuccessfully to get the audio working, I've now upgraded alsa to v 1.0.15 which is supposed to have the 3 patches for the hda-intel that were missing from 1.0.14.  still nothing

I get no error messages when playing files with aplay, totem etc.  alsamixer seems to configure everything fine.  For all debug purposes it seems like the files are being played just no sound is heard.  

any help that anyone could give would be wonderful!

Thanks

---

### Post by Calyce on 2007-10-25
I had something similar on my R61 which is probably pretty the same machine as yours. In my case, the sound was simply muted.

Could you try the following:
1. If you don't have the "Volume Control" applet in you Gnomer panel add it (right click on the panel, select "Add to panel" in the menu, in the new window select "Volume Control" in the "System & Hardware" section then click "Add" and close the window).
2. Start the "Sound Preferences" (menu System -> Preferences -> Sound)
3. Verify that you have "Autodetect" for "Sound Events", "Musci and Movies" and "Audio Conferencing". Verify that you have "HDA Intel (Alsa mixer)" for "Default Mixer Tracks"
4. Click on "Test" in front of "Sound Events"
5. Double click on the "Volume Control" applet we added in the panel on step 1
6. If you don't hear anything, press the multimedia "Volume up" button (the one right on the side of the blue ThinkVantage button).
7. If you still don't hear anything, up the volume in the "Volume Control" applet
8. If you still don't hear anything, make sure PCM is not muted (in that case you will see a red X under PCM, just click on it to unmute).

This procedure worked for me.

BTW, if it's really the same problem as mine, you will see that when you press the multimedia Up and Down button, it is the MIC level that is changed in the "Volume Control" panel.

I hope it will solve your issue.

---

### Post by DrFunn on 2007-11-02
I am using a Lenovo Z61t built in June 2007 running Feisty 7.04  with  2.6.20-16-generic kernel that was updated to the Studio version using synaptic. 

~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]

When I log or out, the ubuntu sound files play nicely and sound great through the laptop speakers or headphones. 
If I go to System > Preferences > Sound > Sound tab >System Sounds 
Play Log out and Log it works even if I am running Firefox. Other's have reported that Firefox hogs their audio. 

However when I start the jack daemon from the command line (using this command string that was suggested to help with JACK working well on the Intel HD audio controller):

~$ jackd -d alsa -p 128 -r 44100 -S true -n 3 &

The system sounds become silent as if JACK is hogging the audio bus.

Applications > Sound & Video > Jack Control to play with JACK

Anyway JACK works in that I can play a beat in Hydrogen and patch it to alsa_pcm and hear the beat, but I am suffering from lots of xruns that seem to make the sound crackly 

 **** alsa_pcm: xrun of at least 4.425 msecs

I have received 90 of these in the last twelve minutes!

I have repeated this with the realtime kernel and still get the same amount of xruns and crackle.

I am going to do a broader search to tweak JACK's settings to reduce the xruns to something reasonable. 

I guess I wanted to say that there is hope that your rig will work soon!:)

   - Dr Funn -

---

### Post by DrFunn on 2007-11-02
Continuing the above thread....

Follow-up on this Z61t is running this version of ALSA:

~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 

Another odd thing is that when I plug my headphones with a boom mike into the laptop jacks they work fine in that I can hear the Hydrogen beat and I can hear myself talking into the boom mike through the headphones. What is odd is that I cannot put any sort of effect  on my voice by connecting alsa_pcm (mic) to Jack Rack in, Jack Rack out to alsa_pcm (speakers). I can only hear the dry voice in the headphones as if they are on a completely different circuit than Jack is using! If I disconnect alsa_pcm (mic) I can still hear my voice...

    - Dr Funn -

---

