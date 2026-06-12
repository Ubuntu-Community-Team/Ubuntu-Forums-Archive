---
title: "alsamixer not saving configuration"
date: 2016-04-25
forum: Multimedia Software
---

### Post by mickee384 on 2016-04-25
Hi

Since doing a fresh install of 16.04, the alsa will not save the configuration. In addition there are 5 (so far) rc.d files in /etc. Like rc0.d, rc1.d, rc2.d for instance. Found out that these are normal. However, everytime I log out or reboot, I have to change alsamixer back as it keeps muting the speakers. [COLOR="#FF0000"]I do not have /etc/rc.d [/COLOR]

I have run ```
sudo alsactl store
``` a few times. Still doesn't save. 

Can I copy one of the rc files to rc.d? Or do I need to create a new rc.d file? Any help would be great!

---

### Post by QDR06VV9 on 2016-04-25
Hi mickee384  I have always used this command.
```
sudo alsactl store 0
```

If that doesn't work, open this file for editing:
Code:
```
gksudo gedit /etc/pulse/default.pa
```


Scroll down to this line: and comment it out
Code:
```
load-module module-device-restore
```
So now it would look like this
```
#load-module module-device-restore
```
Logging out and back in...or even some case's a reboot
Regards

---

### Post by mickee384 on 2016-04-25
Thanks! I will try this and report back. Is the rc.d file created at every reboot? I am concerned as I do not have that, just rc0.d thru rc5.d .

---

### Post by QDR06VV9 on 2016-04-25
I believe that any thing in /etc gets put here by the initial install of the package so No i would not think that it gets a new one from a reboot.

---

### Post by mickee384 on 2016-04-25
so I cannot recreate rc.d then. It's a required file, no?

---

### Post by QDR06VV9 on 2016-04-25
You know I do not have a definitive answer here but I think it is a part of the new systemd that was introduced with 15.10.
One question did you delete any of those rc.d...if you did not then everything should be fine.
But should not have anything to do with why Alsa is not keeping your preferences.

---

### Post by mickee384 on 2016-04-26
No I didn't delete any rc.ds. That said, I don't have the /etc/rc.d

---

### Post by mickee384 on 2016-04-26
> Hi mickee384 I have always used this command.
Code:
```
sudo alsactl store 0
```
If that doesn't work, open this file for editing:
Code:
```
gksudo gedit /etc/pulse/default.pa

```
Scroll down to this line: and comment it out
```

load-module module-device-restore
```
So now it would look like this
Code:
```
#load-module module-device-restore
```
Logging out and back in...or even some case's a reboot
Regards



After these were run, still sound starts muted. Sigh. Thanks for your help. I will keep at it till I figure it out.

---

### Post by QDR06VV9 on 2016-04-26
Dose this work
```
sudo alsa force-reload
```
If not
This is an older thread but should still work.
[URL="http://www.webupd8.org/2009/06/sound-muted-after-restart-in-ubuntu.html"]http://www.webupd8.org/2009/06/sound-muted-after-restart-in-ubuntu.html


[/URL]

---

### Post by mickee384 on 2016-04-29
still not working. When I did the force reload - it reloaded, no errors, but muted the speaker control (which is the only one that actually produces sound) again...sigh.

---

### Post by QDR06VV9 on 2016-04-29
There seems to be a few bugs regarding sound issue's still unresolved.
What make is your sound card?
```
sudo aplay -l
```
and the current kernel you are running.
```
uname  -r
```
I will do my best here...

---

### Post by mickee384 on 2016-05-05
I will get the info later today. Thanks for helping!

---

### Post by mickee384 on 2016-05-05
```
sudo aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1984B Analog [AD1984B Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD1984B Digital [AD1984B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: AD1984B Alt Analog [AD1984B Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [Dream Cheeky Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
uname -r

4.4.0-21-generic

```

hope that helps

---

### Post by QDR06VV9 on 2016-05-09
> **mickee384 said:**
> ```
sudo aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1984B Analog [AD1984B Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD1984B Digital [AD1984B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: AD1984B Alt Analog [AD1984B Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [Dream Cheeky Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
uname -r

4.4.0-21-generic

```

hope that helps
Well the only thing that I see is that maybe this "[Dream Cheeky Audio Device]" might have something to do with not saving levels.
Not sure if you have seen this or not but worth looking at:  [http://usbpiano.sourceforge.net/](http://usbpiano.sourceforge.net/)

And Bear in mind I know nothing of this guy "Lewis Jackson"  So Caution is Advised...but his email is included with that Link
EDIT: I have looked at the source code he provided looks ok to me. **Weather this provides a solution to your problem is still a mystery though. **

---

### Post by mickee384 on 2016-06-02
Thanks, i will try that. The cream cheeky thing is actually a Star Trek (TOS) communicator.

---

### Post by mickee384 on 2016-06-12
Thanks for your reply, No, unfortunately this is still not workinhg. Do you require more information?

---

### Post by kazakore on 2016-06-12
I have this exact same issue on my laptop internal sound card (not tried with my external.) I usually use headphones and they aren't affected if I leave them plugged it at boot but speakers always are (and IIRC the headphones also mute and don't unmute on connection if booted with them not plugged in.) Always worked fine in 14.04

I run everything through Jack into ALSA and am using Ubuntu Studio. PA get doesn't get loaded fully on start but I do load the PA/Jack sincs when Jack starts, which spawns the main process. Pretty sure it is an ALSA issue rather than anything related to PA (although the link earlier seemed not so sure)



sudo aplay -l
```
**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I am not doing anything with and have no way to test the HDMI.

aplay -r 
```
4.4.0-24-lowlatency

```

---

### Post by kazakore on 2016-06-13
[FONT=arial black][SIZE=2]Definitely related in some way to the headphone switch and the fixes mentioned in earlier posts have done nothing to fix it (alsactl store/restore settings including the rc.local line.)

If my headphone are attached then the Speaker output is Muted.
If they are not attached then Headphone output is Muted.
Connecting and removing headhphones once the system is booted does not toggle which is Muted/Active.
But it should not need to. If both are left unmuted then the sounds is killed from the speakers if the headphone plug is in use regardless of AlsaMixer settings. This is how it worked on 14.04.

Is there any other way (than the "alsactl restore" in rc.local)

Is there a difference between the "alsactl restore" command mentioned in the external link posted and the "alsa force-reload" command mention in the thread? Neither seems to make any difference to my setup.[/SIZE][/FONT]

---

### Post by mickee384 on 2016-06-14
shoot! I just realized. The issue I have is Pulse Audio. Sorry about that! But I have the alsa installed as well. Should I remove alsa?

---

### Post by mickee384 on 2016-07-31
as of today, I still haven't figured this out. Sigh. If anyone can help, I can put up more info if requested. Thank so much!

---

### Post by Yellow Pasque on 2016-08-02
> **mickee384 said:**
> The issue I have is Pulse Audio. Sorry about that! But I have the alsa installed as well. Should I remove alsa?

It doesn't make sense to remove ALSA (that's like removing your sound driver). It doesn't make sense to remove pulseaudio either. Even if it's causing the issue (and it may be: [https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Pulse_overwrites_ALSA_settings](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Pulse_overwrites_ALSA_settings) ), a simple workaround would be better:
```
amixer controls
```
For example, if the control is named 'Master', one or both of these commands might accomplish what you want:
```
amixer set Master unmute
amixer set Master 40%
```

Once you've figured out the command(s) to unmute your audio, throw them in a little script and load the script at startup (after pulse loads). I use xfce, so don't ask me exactly how to do that in Unity..

---

### Post by 4tonyland on 2016-08-05
I am having a very similar problem after upgrading from 14.04 to 16.04.  14.04 worked OK.

Computer: HP Pavilion dm1
From AlsaMixer:  
Card: HDA ATI SB
Chip: IDT 92HD87B2/4

Computer boots up with no sound available.
AlsaMixer shows Headphones muted
Unmuting makes sound play through speakers

Plugging in headphones mutes speaker, sound plays through headphones
Unplugging headphones mutes Headphones no sound plays through speakers

Immediately after boot or log out then log in  - running terminal

~$ alsactl restore
alsactl: state_lock:125: file /var/lib/alsa/asound.state lock error: File exists
alsactl: load_state:1683: Cannot open /var/lib/alsa/asound.state for reading: File exists
Found hardware: "HDA-Intel" "ATI R6xx HDMI" "HDA:1002aa01,00aa0100,00100200" "0x103c" "0x3387"
Hardware is initialized using a generic method
Found hardware: "HDA-Intel" "IDT 92HD87B2/4" "HDA:111d76d9,103c3387,00100107" "0x103c" "0x3387"
Hardware is initialized using a generic method
~$ 

Result Headphones unmuted, sound plays through speakers.

This appears to be the same problem as this thread.

PS Another observation that may be helpful.
When I open PulseAudio volume control
Under Output Devices tab
Built in Audio Analogue Stereo
Port set to Headphones (unplugged)  Sound plays through speakers
Port set to Speakers No sound plays through speakers but level bar shows sound playing

Plug in headphones
Port changes to Headphones (plugged in) Sound plays through headphones
Port Speakers (unavailable) 

Unplug headphones
Port returns automatically to Speakers No sound plays through speakers
Set Port to Headphones (unplugged)
Sound plays through Speakers

---

### Post by mickee384 on 2017-02-04
closing. not solved though.

---

### Post by BA3MtEP on 2017-03-26
In case anyone else comes across this issue here is a fix.
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

