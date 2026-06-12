---
title: "Cannot reinstall ALSA. Help, please."
date: 2008-11-05
forum: Multimedia Software
---

### Post by Greasyfingers on 2008-11-05
Oh dear, I seem to have broken part of the universe.

In an attempt to make my front panel microphone record, which I've failed to do using ALSA (everything else seemed to work OK), I gave OSS a whirl, following the guide in this HowTo: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

I did less well with OSS - no microphone input worked at all, and I couldn't get the GUI ossxmix to appear. 

So I attempted to switch back to ALSA by following this post: [http://ubuntuforums.org/showpost.php?p=5539687&postcount=331](http://ubuntuforums.org/showpost.php?p=5539687&postcount=331)
and then using the script linked to in this thread: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)
This is the route linked to in the OSS installation HowTo in order to switch back to ALSA.

But no joy - I just can't get ALSA working again. At all.

I've run 
$ sudo dpkg-reconfigure linux-sound-base
and selected ALSA, and I've gone System -> Preferences -> Sound -> Devices and tried to select ALSA for everything - except it only gives me the option of OSS in the Default Mixer Tracks section. Test sounds only work if OSS is selected - with ALSA selected I get
'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.'

I've rebooted (several times).

If I enter
$ sudo soundon
I get
OSS is already loaded
so it still seems to be in charge.

$ sudo alsa reload
tells me
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

I cannot bring up alsamixer ("function snd_ctl_open failed for default: No such file or directory"), and the GUI volume control is still linked to OSS without an option (File -> Change Device) for ALSA.

ALSA just doesn't seem to be there.

From Synaptic I've reinstalled everything with ALSA in the name, and rebooted, but it always comes back with OSS as the sound driver. At one point Timidity was causing problems with reinstalling ALSA, so I unistalled Timidity, which made the ALSA errors go away, but now Timidity won't reinstall...
'Setting up timidity (2.13.2-19ubuntu1) ...
   ...fail!
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 timidity
E: Sub-process /usr/bin/dpkg returned an error code (1)'

I'm currently in a state of abject confusion, and clearly don't really know what I'm doing.Could someone walk me through a way to uninstall OSS properly and get back to the default state of sound control through ALSA, with Timidity installed too, please?

---

### Post by edyeeh on 2008-11-10
I swtiched to OSS and back and this happened to me as well.

I tried

```
lspci -v
```

and the kernel used is always OSS. I think it has something to do with it. 

alsamixer also puts up this

```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

Now I don't know how to change the kernel back to alsa

---

### Post by quazi on 2008-11-10
Same problem as original poster.  I'm stuck with OSS4 (I installed it from source as well, so I have no method of uninstalling it.)

---

### Post by quazi on 2008-11-10
I tried running "alsaconf", which seems to be working well at first.  However, I get the output ```
modinfo: could not find module snd
modinfo: could not find module snd
modinfo: could not find module snd

```
and it tells me that no PCI card is found.

I also tried a ```
modprobe snd
FATAL: Module snd not found.
FATAL: Error running install command for snd

```

I'm not sure why it wouldn't be able to find the module snd, seeing as ALSA was running fine yesterday.

---

### Post by Kymus on 2008-11-10
I seem to be having a [somewhat similar]("http://ubuntuforums.org/forumdisplay.php?f=334") (yet different) problem after waking up one morning to find out that [my sound was no longer working]("http://ubuntuforums.org/showthread.php?t=974086").

My problem started while trying to follow the instructions on reinstalling ALSA:

The example given for finding the codec was:


```

aplay -l
cat /proc/asound/card0/codec#* | grep Codec
```


yet my results are completely different:


```
kymus@Shouxing:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

regardless, I went forward.

the example mentions modifying the line *options snd-hda-intel model=* in *etc/modprobe.d/alsa-base*, but after opening *etc/modprobe.d/alsa-base*, I didn't find anything with the word "model" in it... :confused::confused:

---

### Post by Greasyfingers on 2008-11-10
Well, I've made a fix - of sorts. I got exasperated enough to do a re-install of Ubuntu. It was a sledgehammer approach, and not really recommended unless you've got about a month of spare time to reconfigure your system back to how it was.

And even after a re-install ALSA seems a bit flakey - the sound is working OK (except I still can't get the front panel mic or streaming audio to record), but a couple of times alsamixer has disappeared, giving the error message "function snd_mixer_load failed: Invalid argument", while opening the Gnome volume control GUI finds it pointing to OSS with no option to select ALSA. So far, a reboot has corrected this each time.

I'm really pretty confused by all this, and I could have done without the need to re-install, but I suppose if the sound output continues to be OK then that's most of what I want.

---

### Post by edyeeh on 2008-11-13
> **Kymus said:**
> I seem to be having a [somewhat similar]("http://ubuntuforums.org/forumdisplay.php?f=334") (yet different) problem after waking up one morning to find out that [my sound was no longer working]("http://ubuntuforums.org/showthread.php?t=974086").

My problem started while trying to follow the instructions on reinstalling ALSA:

The example given for finding the codec was:


```

aplay -l
cat /proc/asound/card0/codec#* | grep Codec
```


yet my results are completely different:


```
kymus@Shouxing:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

regardless, I went forward.

the example mentions modifying the line *options snd-hda-intel model=* in *etc/modprobe.d/alsa-base*, but after opening *etc/modprobe.d/alsa-base*, I didn't find anything with the word "model" in it... :confused::confused:

I've heard of this solution. I tried it but unfortunately it didn't work for me. I think you should be adding the line since its not written there by default.

---

### Post by Kymus on 2008-11-13
> **edyeeh said:**
> I've heard of this solution. I tried it but unfortunately it didn't work for me. I think you should be adding the line since its not written there by default.

I will try that, thank you :)

---

### Post by Toci on 2008-11-14
At least I'm not the only one. 
 And if I try to remove OSS I get "cannot remove oss-linux* : No such file or directory"
 If I try to reinstall it tells me the folders are not empty and when I run "aplay -l" it says I have no sound cards.

 Nothing has worked so far so I'm evaluating reinstalling Ubuntu fully or going back to Windows.

---

### Post by Roasted on 2008-11-14
It's been a while since I ran into this, but I did previously. I tried out OSS4 only to find out it served no additional functionality over Alsa and in fact, it was more of a pain than Alsa was. When trying to switch back I was hit with the same problem.

My solution? Fresh install. 

Go OSS! (lol)

---

### Post by Yellow Pasque on 2008-11-14
Well, since I originally wrote [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) , direct your flames at me :P

If you installed OSS from source, you can uninstall it with:
```
sudo soundoff
sudo sh /<dir where you installed the source>/setup/Linux/removeoss.sh

```

Anyway, uninstalling OSS shouldn't even be necessary to get ALSA working again. In fact, you can alter the OSS soundon script to switch back and forth between them. See this for details: [http://www.4front-tech.com/forum/viewtopic.php?t=2682](http://www.4front-tech.com/forum/viewtopic.php?t=2682)

---

### Post by Kymus on 2008-11-14
> **Temüjin said:**
> Well, since I originally wrote [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) , direct your flames at me :P

If you installed OSS from source, you can uninstall it with:
```
sudo soundoff
sudo sh /<dir where you installed the source>/setup/Linux/removeoss.sh

```

Anyway, uninstalling OSS shouldn't even be necessary to get ALSA working again. In fact, you can alter the OSS soundon script to switch back and forth between them. See this for details: [http://www.4front-tech.com/forum/viewtopic.php?t=2682](http://www.4front-tech.com/forum/viewtopic.php?t=2682)

Temüjin, I could use your input [here]("http://ubuntuforums.org/showthread.php?t=977477"), when you can. I am having trouble with the guide you wrote on reinstalling ALSA.

---

### Post by edyeeh on 2008-11-20
After failing to uninstall OSS and reinstalling ALSA, I gave OSS another chance. I found out the solutions to the OSS problems I've been experiencing from the site of OSS temujin refferred to [http://www.4front-tech.com/forum/]("http://www.4front-tech.com/forum/"). Its very useful finding out OSS problems there rather than ubuntu forums since its their software anyway.

Seems OSS needs some research and studying to get used to compared to the convenience that ALSA gives. After configuring it, OSS works on my system with a few glitches. Not perfect but gives me basic sounds like media player, wine, flash. Just posted this as an alternative if you're thinking of reinstalling ubuntu system or if you have the time.

---

