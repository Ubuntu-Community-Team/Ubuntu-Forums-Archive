---
title: "Help configuring Surround Sound 5.1 and Internal Mic Ubuntu 11.04"
date: 2011-05-18
forum: Multimedia Software
---

### Post by Cyc. on 2011-05-18
Hi all,

I'm running Ubuntu 11.04 on a Dell XPS M1530 laptop, dual boot with windows 7. The soundcard is a HDA Intel SigmaTel STAC9228.

Basically I'm trying to configure Ubuntu so I get 6 channel 5.1 output and can use my internal mic for input. But having great difficulty! :(

There are 3 audio jacks on my laptop, in Windows they can easily be configured for Headphone/Headphone/Mic or Headphone/Headphone/Line-In or Front/Centre/Rear which is what I want.

In Ubuntu under System > Preferences > Sound > Hardware > Profile There are the following options:
[LIST]
[*]Analogue Stereo Input
[*]Digital Stereo Duplex
[*]Digital Stereo Duplex + Analogue Stereo Input
[*]Analogue Surround 4.0 Output
[*]Analogue Surround 4.0 Output + Analogue Stereo Input
[*]Analogue Stereo Output
[*]Analogue Stereo Duplex
[/LIST]

The only profile that recieves input from the internal mic is the last one, Analogue Stereo Duplex, but it outputs Headphone/Headphone/Line-in on the jacks and the input is very quiet even with input volume on max.

I have tried playing around with alsamixer with all of the different profiles but have had no success.

Below is alsa info script output:
[http://www.alsa-project.org/db/?f=0fc25420c0d75a82c84f53f0633ef25361adb6d4](http://www.alsa-project.org/db/?f=0fc25420c0d75a82c84f53f0633ef25361adb6d4)

Any help is greatly appreciated

---

### Post by serbforce on 2011-05-28
I have the very same problem, on my desktop, i have an on board sound card ALC888, and 5.1 speakers, but i am only getting stereo output. And thats pretty much only problem i have with Ubuntu, but a major one.

---

### Post by josecmr on 2011-06-02
I'm having the same problem with my m1530, I tried this: [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound) but to no avail.

---

### Post by SR_ELPIRATA on 2011-06-02
[http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)

---

### Post by lidex on 2011-06-03
> **Cyc. said:**
> Hi all,

I'm running Ubuntu 11.04 on a Dell XPS M1530 laptop, dual boot with windows 7. The soundcard is a HDA Intel SigmaTel STAC9228.

Basically I'm trying to configure Ubuntu so I get 6 channel 5.1 output and can use my internal mic for input. But having great difficulty! :(

There are 3 audio jacks on my laptop, in Windows they can easily be configured for Headphone/Headphone/Mic or Headphone/Headphone/Line-In or Front/Centre/Rear which is what I want.

In Ubuntu under System > Preferences > Sound > Hardware > Profile There are the following options:
[LIST]
[*]Analogue Stereo Input
[*]Digital Stereo Duplex
[*]Digital Stereo Duplex + Analogue Stereo Input
[*]Analogue Surround 4.0 Output
[*]Analogue Surround 4.0 Output + Analogue Stereo Input
[*]Analogue Stereo Output
[*]Analogue Stereo Duplex
[/LIST]

The only profile that recieves input from the internal mic is the last one, Analogue Stereo Duplex, but it outputs Headphone/Headphone/Line-in on the jacks and the input is very quiet even with input volume on max.

I have tried playing around with alsamixer with all of the different profiles but have had no success.

Below is alsa info script output:
[http://www.alsa-project.org/db/?f=0fc25420c0d75a82c84f53f0633ef25361adb6d4](http://www.alsa-project.org/db/?f=0fc25420c0d75a82c84f53f0633ef25361adb6d4)

Any help is greatly appreciated

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=dell-bios" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Next post amixer output:
```
amixer
```

---

### Post by cO5Mo on 2011-09-10
Hello everybody,

until today I had Ubuntu on my laptop only. I was playing with it and using very basic things like Firefox and Skype. After a while and after trying several other distributions I got hooked and installed Ubuntu on my Desktop machine parallel to Windows 7. (This is a BIG step for Windows users)
This means I need to set up more things over time, and I will probably learn a lot during this process. I would say I am an adept Windows user, but a pretty rookie Linux user, yeah I'm a noob XD

So, my problem is kinda similar to the one described here and I did not want to open a new thread.

My mainboard is a MSI P35 Platinum and alsamixer shows Card: HDA Intel and Chip: Realtek ALC888
I have a 5.1 Speaker set connected to the rear jacks and they work fine. BUT:

1.) I cannot separate the front audio jack which I use for headphones from the rear speakers. Meaning whatever comes out of my 5.1 Speakers also comes out of the headphone. There is an option to do this in Windows, but I can't figure out how to configure it in Ubuntu.

2.) I have my TV connected to the rear input jack (blue) to loop it through my computer to the speakers. In Windows 7 there was some option in the HD Audio Manager to use this source.  In Ubuntu I can see the audio level bar moving so the sound from the TV gets to the PC, but it won't play.

I hope somebody has some ideas to fix this. :) maybe this is helpful [http://www.alsa-project.org/db/?f=de4b790fd336cdffc2a78821c37578bc5fcf1574](http://www.alsa-project.org/db/?f=de4b790fd336cdffc2a78821c37578bc5fcf1574)

Thanks in advance

---

### Post by cO5Mo on 2011-09-13
or should i open a new thread?

---

### Post by lidex on 2011-09-14
> **cO5Mo said:**
> or should i open a new thread?

Probably, but I'll answer to that. Try this in a terminal:
```
sudo echo 6stack-dig > /sys/class/sound/hwC0D0/modelname
```
```
sudo echo 1 > /sys/class/sound/hwC0D0/reconfig
```

No help, then this:
```
sudo echo targa-8ch-dig > /sys/class/sound/hwC0D0/modelname
```
```
sudo echo 1 > /sys/class/sound/hwC0D0/reconfig
```

---

### Post by cO5Mo on 2011-10-14
> **lidex said:**
> Probably, but I'll answer to that. Try this in a terminal:
```
sudo echo 6stack-dig > /sys/class/sound/hwC0D0/modelname
``````
sudo echo 1 > /sys/class/sound/hwC0D0/reconfig
```No help, then this:
```
sudo echo targa-8ch-dig > /sys/class/sound/hwC0D0/modelname
``````
sudo echo 1 > /sys/class/sound/hwC0D0/reconfig
```

Hi, thanks for your answer. Just tried it out, but I get this output:

andy@andy:~$ sudo echo 6stack-dig > /sys/class/sound/hwC0D0/modelname
bash: /sys/class/sound/hwC0D0/modelname: Permission denied

So I couldn't even go further with the commands you posted. Any help? Thanks

---

