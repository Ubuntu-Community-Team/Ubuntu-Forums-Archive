---
title: "My microphone does not work"
date: 2009-10-30
forum: Multimedia Software
---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
I need to be able to use skype and sound recorder, but my microphone doesn't work! 
I raised manually the microphone levels, but all I get is static/white noise
Here is the output of **aplay -l **
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Teamgeist on 2009-10-30
Hi.
Have you tried this?

```
sudo apt-get install linux-backports-modules-alsa-karmic
```

Then reboot.

From Daniel T Chen's Blog (Ubuntu Audio Guru):
> Install linux-backports-modules-alsa-karmic (then reboot) if you have a very new computer, because that package enables audio on quite a few very new laptop models and contains much improved support for microphone auto-switching.

[http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Hope that helps somehow.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
That didn't help.It only created microphone 1 and microphone 2, but I get the same result in both entries

---

### Post by MaindotC on 2009-10-30
Same issue, different board and I double checked the pin connections from my case to my mobo:
```

xk@xk:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've been following the directions of the [Sound Troubleshooting Guide](https://help.ubuntu.com/community/SoundTroubleshooting) and from what I read on the ALSA site my chipset is supported.  I am at the part where the guide starts to add configuration options to /etc/modprobe.d/alsa-base.conf but I'm not sure what options to put in there.  Also, there is no linux-restricted-modules package for Karmic.  You can find my alsa configuration at [http://is.gd/4Igd4](http://is.gd/4Igd4)

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
The package exists in synaptic , do a search
Also I am on a laptop, so I cannot really check the board

---

### Post by MaindotC on 2009-10-30
> **&#1057 said:**
> The package exists in synaptic , do a search

Not on my version of 9.10:
```

xk@xk:~$ sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
[sudo] password for xk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.31-14-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.31-14-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

xk@xk:~$
```

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
Open synaptic and type backports.I see it there
Also did you apt-get updated  ? 

The exact name is indeed linux-backports-modules-alsa-karmic-generic 

For some reason it doesn't appear in apt-get and aptitude

---

### Post by MaindotC on 2009-10-30
Can you please stop w/ the Synaptic??  It's not there! No matter what package manager you use!  I enabled backports repo and that package isn't there.  There is no restricted modules package for Karmic!!

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
That's strange! Is there a problem with the repositories?

---

### Post by MaindotC on 2009-10-30
No, but I've searched for that package before because it's usually just modules and it won't affect my system unless something needs it so I install it anyway.  I tried when I first installed Karmic.  It must have been relinquished or something.  Maybe if I was on the mailing lists I'd know about this stuff.

So did you try the sound troubleshooting guide?

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
My sound card works perfectly, only my microphone doesn't .
I am running the latest version of alsa
Here is alsainfo: 

[http://www.alsa-project.org/db/?f=bf5df288c2dee1c9d2984e9e61315d1ccf5c040f](http://www.alsa-project.org/db/?f=bf5df288c2dee1c9d2984e9e61315d1ccf5c040f)

---

### Post by MaindotC on 2009-10-30
Well, isn't the microphone part of the sound card?

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
Okay I need to clarify:
The input doesn't work and the output works

---

### Post by MaindotC on 2009-10-30
Exactly.  My very same issue.

---

### Post by andied on 2009-10-30
same for me...and a few thousand others I suspect. Very frustrating: I really like Ubuntu (and especially Karmic) but cannot use it if I am unable to use Skype(also tried and like Kubuntu, but again, no usable mic). I have read dozens of threads on this issue and tried numerous fixes and tweaks, but cannot get the mic to work, so I will stick to XP until and if this gets solved.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
TIP:  If you have a spare set of earphones you can use them as an external microphone.

---

### Post by Relysis on 2009-10-30
This may not help you, but I had the same problem.  I did a clean install of Ubuntu 9.10, and installed skype 2.1.  I got sound output, but no mic.  I got it to work by going into sound preferences, the hardware tab, then selecting 'Analog Stereo Duplex' from the profile menu.  Then under the input tab I selected the 'Internal Audio Analog Stereo' device, and the 'Microphone 1' connector.  

This completely fixed my problem.  I was also worried about the pulseaudio-only options in skype beta, but it works great now.  I hope this helps.

---

### Post by hogu on 2009-10-31
> **Relysis said:**
> This may not help you, but I had the same problem.  I did a clean install of Ubuntu 9.10, and installed skype 2.1.  I got sound output, but no mic.  I got it to work by going into sound preferences, the hardware tab, then selecting 'Analog Stereo Duplex' from the profile menu.  Then under the input tab I selected the 'Internal Audio Analog Stereo' device, and the 'Microphone 1' connector.  

This completely fixed my problem.  I was also worried about the pulseaudio-only options in skype beta, but it works great now.  I hope this helps.

I have the same problem, output is fine, input isn't.  I switched to analog stereo duplex, but I don't see any connector selector for input, only output.  does anyone know why that is?

thanks!

---

### Post by hellmitre on 2009-10-31
Both audio output and input work if I do this -- but output I frequently get blips of static which makes it really hard to be satisfied with this functionality. Anyone hear of this or have this happen to them? I've tried literally every other configuration in the Sound Preferences > Hardware tab.

---

### Post by hogu on 2009-10-31
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

look at the link for Alsa configuration .txt they have notes about the specific option, for my card, snd-hda, there were some options recommended if you get pops, but i don't know what your model is.

---

### Post by hogu on 2009-10-31
ok, I installed karmic backports package for alsa modules and now my mic is working  - it sounds a real noisy though... but anyways, it works.

---

### Post by MaindotC on 2009-10-31
> **hogu said:**
> [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

look at the link for Alsa configuration .txt they have notes about the specific option, for my card, snd-hda, there were some options recommended if you get pops, but i don't know what your model is.

I already stated this in post #3...

> **hogu said:**
> ok, I installed karmic backports package for alsa modules and now my mic is working  - it sounds a real noisy though... but anyways, it works.

What is this "backports" modules package that you all are talking about?!?! I enabled the backports repository but I can't find the package stated in the sound troubleshooting guide:
```

linux-ubuntu-modules-`uname -r`

```
What is the exact name of the module you installed ?!?!

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-31
> **Relysis said:**
> This may not help you, but I had the same problem.  I did a clean install of Ubuntu 9.10, and installed skype 2.1.  I got sound output, but no mic.  I got it to work by going into sound preferences, the hardware tab, then selecting 'Analog Stereo Duplex' from the profile menu.  Then under the input tab I selected the 'Internal Audio Analog Stereo' device, and the 'Microphone 1' connector.  

This completely fixed my problem.  I was also worried about the pulseaudio-only options in skype beta, but it works great now.  I hope this helps.

I am on the same setting, but it doesn't work

---

### Post by Teamgeist on 2009-10-31
> **strAlan said:**
> I already stated this in post #3...

What is the exact name of the module you installed ?!?!

The package name is linux-backports-modules-alsa-karmic-generic

So do a ```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
``` or do it via Synaptic.

I recommend to uncheck the Backports Repository. This will do more harm than good in the long run.

---

### Post by MaindotC on 2009-10-31
> **Teamgeist said:**
> The package name is linux-backports-modules-alsa-karmic-generic

So do a ```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
``` or do it via Synaptic.

I recommend to uncheck the Backports Repository. This will do more harm than good in the long run.

I did install this package WITHOUT enabling the backports repository and now my microphone works.  Thank you for the suggestion!  Russian - what's the status of your issue?

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-11-01
I have installed the same package from universe, but it doesn't work.

---

### Post by MaindotC on 2009-11-01
Well are you documenting your steps?  Did you try different profiles?

---

### Post by MaindotC on 2009-11-26
Actually, it WAS working for like 2 seconds (just enough for me to breath into it to test) and now for some reason it doesn't...

---

### Post by hyperhelium on 2009-11-26
Hi

I upgraded to Karmic from Jaunty, and then I upgraded Skype to version 2.1. I'm using a laptop and I had most of the same problems people are having here. When I finally managed to have the microphone working, it had a very poor sound quality and there was a lot of noise in the mic of the headset.

What I did was adjusting the levels of the Mic in the Pulse Audio Device Chooser, and lower the input levels. They seemed to be too high.

Now it works perfectly.

I hope it helps.

---

### Post by kinggo on 2009-11-27
Well, I'm another one with mic issue. 
I'm using HP tx100 and all was fine in 9.04. After upgrade to 9.10 mic stopped working. I did a fresh install then and nothing again. I also installed karmic on one Toshiba A200CR and one Lenovo G530. They both have microphone under "sound- input device". Lenovo has built-in one and Toshiba has one on the headset and one on the webcam (I can see both of them and both working). Both of those computers have Intel chipset.
My tx100 has nVidia.

So what I did is this. First I enabled "multimedia systems selector" in the main menu. From there I can select ALSA as my default input. 
After that I still cannot see microphone option in "sound preferences- input" but if I press test in Mutimedia System Selector I can se that my mic levels are changing and I can record my voice finally. 

My "sound preferences" are set to analog stereo duplex although this is not the best solution for me 'cause I used my optical output in Jaunty and now I have to switch between Analog stereo and Digital all the time. If digital is set then my laptop speakers don't work, if analog is set then digital output don't work. I can't find the way to fix this. Generally, PULSE sux, who needs sound server anyway for daily use? I think it's related somehow to GNOME because there are similar issues with other distros I tried and all of them were GNOME.

---

### Post by TDK800 on 2009-11-27
Strannik, try this, fixed the mic, for Skype too, and got pulseaudio still installed: [http://ubuntuforums.org/showthread.php?p=8397068](http://ubuntuforums.org/showthread.php?p=8397068)

---

### Post by arphaya on 2009-12-01
Hi!

I have recently switched from windows to ubuntu 9.10 and as it is the case with numerous others, neither my inbuilt mic of my sony laptop nor the headset mic works.

I have installed                                 
linux-backports-modules-alsa-2.6.31-15-generic
and also the newest version of pulseaudio. (and see both of them in the synaptic package manager)

I have tried all possible options (mic1, mic2 and line-in) of the sound preference in the system menu and also tried to turn up all mic-settings (not muted and an enhancement in the red region) when running $ alsameter and checking then with $ pavumeter --record.

I do see activity recorded when I plug in my microphone, but do not hear this or any other sound from the mics.

Well, thats the case with me and I am looking forward to try other options...

Cony

---

### Post by Zenith88 on 2009-12-01
For me the microphone issue appears to be purely Pulse Audio related.
I just moved from Fedora 12 (where nothing at all worked) to Ubuntu Studio 9.10 where so far only microphone capture in Skype does not work.

I solved that problem in Fedora by uninstalling Pulse Audio. With PA installed Skype had only PA devices in the Sound Devices tab. Once uninstalled, it allowed me to choose Default for output and Audigy2 microphone capture for input and worked fine.

A very angry developer from Fedora project told me to use pasuspender to launch Skype instead of uninstalling PA, but it apparently does not work - Skype still only shows PA devices in the sound options.

So in a few seconds PA goes into the trashcan and I'll report back either way.

Edit: Uninstalling PA completely fixed Skype. The only annoyance is that now I don't have a mixer on the task panel, but I can live with that. Now if only I was able to determine the root cause. Is it emu10k driver, or PA problem?

Now the only microphone related problem remaining is notorious 0.6 second recording in Audacity.

> **TDK800 said:**
> Strannik, try this, fixed the mic, for Skype too, and got pulseaudio still installed: [http://ubuntuforums.org/showthread.php?p=8397068](http://ubuntuforums.org/showthread.php?p=8397068)

Unfortunately that will not work for every user. What the link is discussing is updating to a new version of kernel. That is generic Ubuntu kernel, while for example, yours truly runs Ubuntu Studio sporting its own low latency preemptive kernel.

---

