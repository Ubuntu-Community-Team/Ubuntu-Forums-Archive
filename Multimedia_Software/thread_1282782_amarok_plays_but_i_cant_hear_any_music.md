---
title: "amarok plays but i cant hear any music"
date: 2009-10-04
forum: Multimedia Software
---

### Post by jarrah-95 on 2009-10-04
im not going deaf (i can still hear people talking) but when i try to play music in amarok it says its playing but no music plays. i dont think this has anything to do with amarok as i cant hear the gdm making sound when i turn the laptop on eather. the other thing i have noticed is that when i try to listen to music in rhythm box it just wont play.
thanks

---

### Post by tuxxy on 2009-10-04
Do you hear the test sound files play in sound prefs?  ALso make sure your volume is up on alsamixer.  Enter this in terminal;

```
alsamixer
```

---

### Post by jarrah-95 on 2009-10-04
no sound in the test ans i have just turned up the volume in alsamixer 
also i have used to sticky at the top of multymedia and video to reinstall alsa so its new and clean

---

### Post by tuxxy on 2009-10-04
In that case what sound card are you using.

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by jarrah-95 on 2009-10-04
this is the relavant part of my lspci -v output
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Device 30a5                                                
        Flags: bus master, fast devsel, latency 0, IRQ 22                                             
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]                                      
        Capabilities: <access denied>                                                                 
        Kernel driver in use: HDA Intel                                                               
        Kernel modules: snd-hda-intel      

```
do you want me to post the output it says to on that page

---

### Post by chitowner2 on 2009-10-07
I'm going to jump in here because I have a similar problem, but in my case rhythmbox plays my mp3's just fine, so this is not a hardware problem. 

When I switch to amarok however, I get no audio. 

It was working normally a while back, but I added some codecs needed for video, in the process changing the default audio to alsa, but I thought that was only for SMplayer and Mplayer. 

Ideas anybody? Why does rhythmbox play but amarok not??

Thanks,
CT

AHA!
Fixed!
Settings > configure Amarok > Playback > Sound System > Configure > choose Pulse Audio (test!) > save settings.
Works!

---

### Post by jarrah-95 on 2009-10-08
good that you have got yours to work and i have to mine just randomly started to work

---

### Post by chitowner2 on 2009-10-08
> **jarrah-95 said:**
> good that you have got yours to work and i have to mine just randomly started to work


I know this is trivial, but often it corrects odd problems for unknown reasons if you just reboot....  sometimes logging out and back in is sufficient. If that works, you won't know why, but so what?

:-/
CT

---

### Post by jarrah-95 on 2009-10-08
i know why that works but that isnt what happened i think it was an update. nut rebooting helps as it deleates the data stored in the ram and this means that if there was an error in the code in the ram it is gone
thanks

---

