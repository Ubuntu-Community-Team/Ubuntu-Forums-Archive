---
title: "Pulseaudio Volume control problem"
date: 2009-12-19
forum: Multimedia Software
---

### Post by afrodeity on 2009-12-19
I changed the settings in pavucontrol, one of the configurations or input/output. Thinking maybe there was a better sound option. Instead, my volume control applet in the panel disappeared, and if I try to open pavucontrol, it tells me "**Connection failed, Connection refused**"


Now pulseaudio itself seems to have a problem
```


pulseaudio
E: module-udev-detect.c: Failed to get card object.
E: module-ladspa-sink.c: Master sink not found
E: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master= plugin=mbeq_1197 label=mbeq control=0.0,0.0,0.0,0.0,0.0,-4.5,-10.0,-6.0,0.5,1.0,2.0,4.0,4.0,0.0,0.0"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.


```

I found some more info on [Karmic Sound Issues ]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") and there was definitely a problem with Timidity grabbing the sound before pulseaudio. I have now removed timidity, but pulseadio still not working. I have sound, but it appears to be just alsa.Is there a way of manually changing the pavucontrol configuration?

Any clues?

---

### Post by afrodeity on 2009-12-19
```
$ killall pulseasudio
pulseasudio: no process found

```

System > Sound

Waiting for sound system to respond

I have sound but no pulseaudio server and no volume icon!

---

### Post by afrodeity on 2009-12-19
still nothing 

[http://translate.googleusercontent.com/translate_c?hl=en&sl=es&tl=en&u=http://ubuntuforums.org/showthread.php%3Ft%3D1305889&rurl=translate.google.com&twu=1&usg=ALkJrhjpPkvr3luZat99jCbOwSJ5GVx_4g](http://translate.googleusercontent.com/translate_c?hl=en&sl=es&tl=en&u=http://ubuntuforums.org/showthread.php%3Ft%3D1305889&rurl=translate.google.com&twu=1&usg=ALkJrhjpPkvr3luZat99jCbOwSJ5GVx_4g)

---

### Post by afrodeity on 2009-12-21
@#$%^&*& pavucontrol

```

OPTIONS
       pavucontrol does not accept any options.

```

---

### Post by afrodeity on 2009-12-21
I installed pavdev applet, following advice from somebody on the ubuntu users mailing list. No luck. If I open the manager it says says **failure: connection refused** at the bottom. If I try to connect, there is nothing to connect to. It can't see any sinks or sources. No clients or devices. Volume control still opens up with** Connection Failed: Connection refused**. There must be a way to reset the default input/output options which are causing the problem?

---

### Post by afrodeity on 2009-12-21
System > Preferences > Sound **Waiting for Sound System to Respond**

But no response.

I've tried toggling off Pulseaudion in startup applications, restarting, toggling back on. But no go.

---

### Post by VertexPusher on 2009-12-21
> **afrodeity said:**
> E: module-udev-detect.c: Failed to get card object.
It seems that PulseAudio has trouble detecting your sound card.

Does ALSA detect it? Check the output of
```
aplay -l
```
There should be at least card 0, maybe more. If the first card listed is not card 0, ALSA failed to initialize properly. In that case,
```
sudo alsa force-reload
```
will help. If no sound cards are listed at all, check the output of
```
lspci
```
to see if the card appears there. If your card is a USB audio interface, check
```
lsusb
```
instead.

If card 0 is available, you can use
```
speaker-test -t wav -c 2 -D plughw:0
```
to test it.

---

### Post by garvinrick4 on 2009-12-21
Look towards bottom of this post, it seems it happens quite a bit.



I just uninstalled did a "sudo apt-get clean" without qoutes and then installed and it
stopped doing the same thing.

  	 	 	 	 	 	  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR]

7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect![/SIZE][/FONT][/COLOR]

---

### Post by afrodeity on 2009-12-21
> **VertexPusher said:**
> It seems that PulseAudio has trouble detecting your sound card.

Does ALSA detect it? Check the output of
```
aplay -l
```
There should be at least card 0, maybe more.
instead. [/code]

Yes, card 0

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

> 
If card 0 is available, you can use
```
speaker-test -t wav -c 2 -D plughw:0
```
to test it.

```



speaker-test 1.0.20 device busy

Playback device is plughw:0
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy

```

---

### Post by afrodeity on 2009-12-21
> **garvinrick4 said:**
> Look towards bottom of this post, it seems it happens quite a bit.



I just uninstalled did a "sudo apt-get clean" without qoutes and then installed and it
stopped doing the same thing.

  	 	 	 	 	 	  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]

...........

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR]

7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect![/SIZE][/FONT][/COLOR]

**I get a slightly different error**

```

 pulseaudio & pavucontrol
[1] 32418
E: module-alsa-sink.c: Failed to parse module arguments
E: module.c: Failed to load  module "module-alsa-sink" (argument: "control = PCM "): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
[1]+  Exit 1                  pulseaudio

```

---

### Post by afrodeity on 2009-12-21
Which has to do with PCM control

Had to undo this "fix" from earlier attempt at fixing:

> 
 sudo nano /etc/pulse/default.pa sudo nano / etc / pulse / default.pa 

Uncomment the line : #load-module module-alsa-sink Uncomment the line: # load-module module-alsa-sink
And add: control=PCM And add: control = PCM
So it reads: load-module module-alsa-sink control=PCM So it reads: load-module module-alsa-sink control = PCM 


---

### Post by joe.schaefer on 2010-01-05
Sorry about reporting a problem with the pulseaudio libraries!

It turned out to be a problem with the loudspeakers. A different pair of loudspeakers solved it. There was no problem with the recently updated libraries whatsoever.

My bad! 

Joe Schaefer

---

### Post by jayeseay on 2010-01-30
I had a similar problem but it was due to permissions of the virtual sound user space. 

either removing or changing sound systems had no effect - removing pulse stopped certain programs from running audio ...

while moving home I changed some of the permissions around and the .gvfs folder was done while using sudo chmod / chown on my home folder ....

had to use root login in order to fix the problem 

by giving it back its permissions to - others to access it (read privledges) ... sound in firefox had dropped in a video ... 

not sure if this was the exact reason why - but configuration files always end up getting left behind from removals of certain things and during the installation of a package it will keep the links pointing to certain sources .. 

the output of the alsa force reload was the solution as it complained about not having access to the folder / or gvfs ...

my problems have only been directly related to deb packages that I installed for earlier software - waiting for the next LTS release 

in some cases the sound glitches after a period of time and then returns to normal as it is dropped for some unknown reason...

---

### Post by afrodeity on 2010-03-23
Back here again, because I changed one of the settings and the whole system just borked.

```

pulseaudio & pavucontrol
[1] 18317
E: module-udev-detect.c: You apparently ran out of inotify watches, probably because Tracker/Beagle took them all away. I wished people would do their homework first and fix inotify before using it for watching whole directory trees which is something the current inotify is certainly not useful for. Please make sure to drop the Tracker/Beagle guys a line complaining about their broken use of inotify.
E: module-udev-detect.c: You apparently ran out of inotify watches, probably because Tracker/Beagle took them all away. I wished people would do their homework first and fix inotify before using it for watching whole directory trees which is something the current inotify is certainly not useful for. Please make sure to drop the Tracker/Beagle guys a line complaining about their broken use of inotify.
E: module-ladspa-sink.c: Master sink not found
E: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_80_01.0.analog-stereo plugin=mbeq_1197 label=mbeq control=6.1,4.3,4.3,1.7,1.7,1.7,-0.1,-0.1,-0.1,0.8,-10.7,-14.2,-15.1,-7.2,0.0"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
[1]+  Exit 1                  pulseaudio

```

---

### Post by afrodeity on 2010-07-02
```
rm -r ~/.pulse
```

```
sudo killall pulseaudio
sudo pulseaudio --system --daemonize
```


This is helpful:[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Reason I back here again is last round of gstreamer updates borked the sound. Another release 12 hours later giving me excellent sound, but had to deal with the damage. Love the wild world of foss:)

---

### Post by lilychef on 2010-07-03
Holy cow!  Why is this even an issue???  As much as I hate Windows and Apple, issues like these are enuff for me to throw in the towel and go back!  I mean, I love the independent spirit of Ubuntu, and the fact that it is open-sourced and a wonderful, fast interface, but dammit - I'd like to actually listen to audio NORMALLY and change my sound settings!  Ha!  isn't that like a REALLY SIMPLE THING for a computer to be able to do??  ESPECIALLY when it worked PERFECTLY for so long, only to have a simple update come along and screw it all up?????? I'M SO FRUSTRATED!  I mean, get it together, people!

For reference:
[http://ubuntuforums.org/showthread.php?t=1522234](http://ubuntuforums.org/showthread.php?t=1522234)

---

### Post by afrodeity on 2010-07-03
Guess this is the price we pay for being on the bleeding edge. The gstreamer developers ppa is not sanctioned by Ubuntu and is thus comes without any guarantee.

Plus side is I get to play with some of the advances being made with gstreamer.

For example: gstreamer-webcam

available from
```

#Gstreamer Webcam Rick Spencer PPA
deb http://ppa.launchpad.net/rick-rickspencer3/ppa/ubuntu lucid main #Gstreamer Webcam Rick Spencer PPA
deb-src http://ppa.launchpad.net/rick-rickspencer3/ppa/ubuntu lucid main #Gstreamer Webcam Rick Spencer PPA

```

---

### Post by afrodeity on 2010-07-03
> **afrodeity said:**
> Guess this is the price we pay for being on the bleeding edge. The gstreamer developers ppa is not sanctioned by Ubuntu and is thus comes without any guarantee.

Plus side is I get to play with some of the advances being made with gstreamer.

For example: gstreamer-webcam

available from
```

#Gstreamer Webcam Rick Spencer PPA
deb http://ppa.launchpad.net/rick-rickspencer3/ppa/ubuntu lucid main #Gstreamer Webcam Rick Spencer PPA
deb-src http://ppa.launchpad.net/rick-rickspencer3/ppa/ubuntu lucid main #Gstreamer Webcam Rick Spencer PPA

```

PS: But there is a nasty bug in the system which results from changing the profile configuration from analog output to digital. Result is pulseaudio has to be killed and restarted.

---

### Post by lilychef on 2010-07-04
X

---

### Post by lilychef on 2010-07-04
> **afrodeity said:**
> ```
rm -r ~/.pulse
```

```
sudo killall pulseaudio
sudo pulseaudio --system --daemonize
```


This is helpful:[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Reason I back here again is [COLOR="Red"]**last round of gstreamer updates borked the sound. **[/COLOR]Another release 12 hours later giving me excellent sound, but had to deal with the damage. Love the wild world of foss:)

What do you mean by "borked the sound"?  I have said that an update caused my issue of "waiting for sound system to respond" and loss of volume control functionality...  Could there be a connection?

I went to that link for help with Pulseaudio, but it doesn't mention Lucid...  Things are definitely different in Lucid... I had completely different sound panel controls, etc. when I upgraded and before this latest crash...  and my surround sound worked PERFECTLY for the first time in Ubuntu...

---

