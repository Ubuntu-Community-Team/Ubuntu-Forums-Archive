---
title: "Sound working very inconstantly with videos!"
date: 2010-03-04
forum: Multimedia Software
---

### Post by ursl on 2010-03-04
Ok, I just built a new system and installed Kubuntu. I'm having some sound problems, but they are very strange. 

First sound worked fine out of the box, played a DVD fine, flash video, fine. The only trouble I was having was some static/interference which I assume is from the onboard sound not being the best.

Then I went to play a flash video, and I got no sound, just some slight static (from the onboard sound?)
Played a DVD - no sound
Restarted, Kubuntu played its opening tune, I heard it, but STILL no DVD sound or flash video sound. 
Emptying recycle bin sound ok.
I played an mp3, music plays fine. 

So I figured I'd figure it out later and went to go do something else. Later in the day I opened a flash game, and THERE WAS SOUND. Weird. Opened a DVD, sound. Flash video, sound. Yay! It fixed itself!

Later on, I go to play another flash video (after not using anything with sound at all for a bit) and I don't get any sound again! Opened DVD, no sound. But I opened a song and I have sound there still. Kubuntu still plays a sound when loading KDE and emptying the recycle bin.

It hasn't moved itself from the no sound stage again yet. I installed about 24 hours ago.

```
lspci -v
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Giga-byte Technology Device a102                               
        Flags: bus master, fast devsel, latency 0, IRQ 22                         
        Memory at fbff8000 (64-bit, non-prefetchable) [size=16K]                  
        Capabilities: <access denied>                                             
        Kernel driver in use: HDA Intel                                           
        Kernel modules: snd-hda-intel

``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1                                                 
  Subdevice #0: subdevice #0                                      
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1                                                   
  Subdevice #0: subdevice #0

```I don't know where the start troubleshooting this.
Thanks!

---

### Post by ursl on 2010-03-04
Sorry, here it is again with the access denied stuff
```
sudo lspci -v
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: Giga-byte Technology Device a102                               
        Flags: bus master, fast devsel, latency 0, IRQ 22                         
        Memory at fbff8000 (64-bit, non-prefetchable) [size=16K]                  
        Capabilities: [50] Power Management version 2                             
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00            
        Capabilities: [100] Virtual Channel <?>                                        
        Capabilities: [130] Root Complex Link <?>                                      
        Kernel driver in use: HDA Intel                                                
        Kernel modules: snd-hda-intel                                                  

```

---

### Post by ursl on 2010-03-04
Update:
I downloaded Songbird, tried to play a mp3, no sound.
Tried to play in various players:
Amarok has sound.
VLC - no sound

---

### Post by ursl on 2010-03-05
No ideas? :(

---

### Post by andrewthomas on 2010-09-25
[http://ubuntuforums.org/showpost.php?p=9889479&postcount=3](http://ubuntuforums.org/showpost.php?p=9889479&postcount=3)

---

