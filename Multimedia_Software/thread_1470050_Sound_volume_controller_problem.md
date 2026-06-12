---
title: "Sound volume controller problem"
date: 2010-05-02
forum: Multimedia Software
---

### Post by smartbei on 2010-05-02
When I open the sound configurations dialog (either through the system tray icon or through preferences), it comes up just fine. After a couple seconds (doesn't really matter what I do), it freezes, and a box comes up with "waiting for sound system to respond".

When this happens the volume control icon shows '---' instead of the volume, and though I can still play sound, only from a single device at a time.

Logging off and logging back in fixes the problem, but only until I open the configuration box.

The drivers appear to be installed fine, and everything is maxed in alsamixer (though since I have sound that obviously isn't the problem).

I have been unable to find the problem on my own - would be really glad if you guys could help.

EDIT: If I restart pulseaudio, I am able to hear sound from more than one application, but I still can;t get the sound configuration dialog to show.

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by smartbei on 2010-05-06
Sorry about the delay - here it is:
```

$ uname -a
Linux ********* 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

```
```

$ head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1708

```
I am running a generic PC - no meaningful make or model. 

Thanks for the help!

---

### Post by lidex on 2010-05-06
Firstly do this:
```
sudo apt-get update
sudo apt-get upgrade
```
Reboot.
To get your system updated to latest kernel.

---

### Post by smartbei on 2010-05-07
Did that.
Now, the volume still looks like [IMG]http://img683.imageshack.us/img683/5361/screenshotfqc.png[/IMG] but I can open the Sound Preferences dialog (it doesn't freeze).

Instead, it doesn't seem to recognize any devices, even though when this happens all the commands return the same as they did before.

I restarted pulseaudio, and the dialog was working again, but then I had wierd problems with amarok - if I muted amarok or turned its volume down through the sound control dialog, amarok would start to use 100% of both cpu cores, and stop playing music. If I killed amarok, the sound control dialog would behave as in the beginning (freezing, etc.) Very odd.

Thanks!

---

### Post by lidex on 2010-05-08
Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot.

---

### Post by smartbei on 2010-05-08
I followed part A, but I keep getting Connection failed: Connection refused, and pulseaudio IS running (it tells me it cannot start because the daemon is already running. Also, I didn't have any of the asound files that are deleted in the beginning.



A little later I could open the volume control, but under output I see "Dummy Output."

I installed the alsa backports, but I am not sure how to check if that helped or not. Everything looks the same.

Thanks for helping!

---

### Post by lidex on 2010-05-08
What is this showing now:
```
aplay -l
```

And what is the status of your sound now, (be specific)?

---

### Post by smartbei on 2010-05-08
Status of sound?
Amarok works when I tell it to use the device itself as output. Pulseaudio apparently does not work.

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: VT82xx [HDA VIA VT82xx], device 1: VT1708 Digital [VT1708 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2010-05-08
Do you have sound in other apps, system sounds, etc? You're using gnome, correct?

---

### Post by smartbei on 2010-05-14
Rythmbox behaves oddly - it starts to play the sound (I can hear it fine), but after 3 seconds or so I get a CPU usage spike and the song stops. I can restart it, but the same thing happens.

Sound in flash does not work once the volume symbol looks as in the image above, but does work before.

---

### Post by lidex on 2010-05-14
What happens with these from Alt+F2 run box:
```
pavucontrol
```
```
gnome-volume-control
```

---

### Post by smartbei on 2010-05-15
The Alt-F2 run box I assume :-).

**When nothing has crashed yet:**
Now I can't hear pulseaudio sound at all. For example, on a youtube video I can see in pavucontrol that it is outputing sound, but I can't hear it. Ditto in gnome-volume-control.

**When it has crashed already**
pavucontrol crashes on opening, with the same error as above. gnome-volume-control allows me to select different devices, some of which work, some crash it (apparently).

Very odd behavior.

Thanks again for your help!

---

### Post by smartbei on 2010-05-15
I think I got it working - I tried a different output device in gnome-volume-control and now it looks like sound is working and mixing fine.

Input doesn't work at all, and if I try to change the device so that it would, everything falls apart as above. So I will live without input for now - I don't record anyway.

---

### Post by lidex on 2010-05-16
Hmm...F2 you say. I'll have to try that :oops:

I've seen some issues lately with Rhythmbox. This may be of service:
```
sudo cp /usr/lib/libtotem-plparser.so /usr/lib/libtotem-plparser.so.12
```

Also make sure gstreamer is up to par. --PART 1/5, ESSENTIAL PACKAGES-- here:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

