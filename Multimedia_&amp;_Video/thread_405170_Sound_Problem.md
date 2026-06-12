---
title: "Sound Problem"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by locolbd on 2007-04-09
Hey i am fairly new to ubuntu

I have both ubuntu and windows on the same computer.  However i have a problem with the sound while am loggin into ubuntu.  The sound is very low and all the volume controls that i can find are maxed.  

However when i log into windows, the sound works normal.  Can anyone give a solution to my problem. By the way am using v. 7.04 Feisty

HINT HINT: In windows there are two catergories in the sound control i use to alter sound "Wave and the Master Volume" in ubuntu i do not see wave"

thanks in advance

---

### Post by heimo on 2007-04-09
Double click on Volume controller (speaker icon).  Select Edit->Preferences and make sure you have all necessary tracks checked. If that doesn't work, open a terminal window (Applications->Accessories->Terminal or alt+F2 and type "gnome-terminal" -> Run) and run alsamixer in terminal. Use arrow keys to select different tracks, tabulator to select different set of tracks, up arrow to add volume and key M to mute / unmute tracks.

Does it solve too low volume problem?

---

### Post by locolbd on 2007-04-09
well thanks a million for the reply, i did what you said but still am having problems.

in the terminal i see "MASTER<>PCM<>MIC<>CALLLER 1<>OFF HOOK"

Mater is right down, and the arrow keys cannot bring it up so is caller 1 and off hook.
i can bring mic up but that isnt worth much for playback anyways and pcm is the only thing 
i can move and that is what affects sound, but it was maxed so the only thing i did was bring
the volume down, brought it to its maximum position but the sound is still the same .

very low

---

### Post by heimo on 2007-04-09
That's strange. Would you run commands below and give us the output:
```

lspci | grep -i "audio\|snd"
aplay -l

```

Oh, and check if you have any other devices / sliders available in the graphical volume contoller, under File -> Devices menu.

---

### Post by locolbd on 2007-04-09
# lspci | grep -i "audio\|snd"
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and there are no more sliders, i checked for all of those things before i published my post

regards
 hope you guys are able to help

---

### Post by heimo on 2007-04-10
I'm out of ideas. I've also got Intel HDA chip, and audio works fine.

Maybe you could try to restore my slider settings (see attachment). 
```

gunzip asound.state.gz
alsactl -f asound.state restore
```[ATTACH]29375[/ATTACH]

---

### Post by locolbd on 2007-04-10
> **heimo said:**
> I'm out of ideas. I've also got Intel HDA chip, and audio works fine.

Maybe you could try to restore my slider settings (see attachment). 
```

gunzip asound.state.gz
alsactl -f asound.state restore
```[ATTACH]29375[/ATTACH]
# alsactl -f asound.state restore
alsactl: set_control:991: warning: name mismatch (Front Playback Volume/Master Playback Switch) for control #1
alsactl: set_control:993: warning: index mismatch (0/0) for control #1
alsactl: set_control:995: failed to obtain info for control #1 (Operation not permitted)


this an error i recieved after tryin to restore

---

### Post by heimo on 2007-04-10
Ok, that wasn't quite compatible idea. :) How about, use alsactl store command with -f flag to write a configuration file, open it and check the values. You could even try to edit it directly and restore.

---

### Post by ned99 on 2007-04-18
Hi I'm having the same problem with the same soundchip and I was wondering if you found a solution?

Thanks.

---

### Post by locolbd on 2007-04-18
Yes i did find a solution a solution actually it is real simple just click on the following link and that should help you through.  If you are still having problem feel free to post a reply i can walk you through the process.  
[http://ubuntuforums.org/showthread.php?t=405065](http://ubuntuforums.org/showthread.php?t=405065)

---

