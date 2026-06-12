---
title: "Ubuntu 10.04 sound problems"
date: 2010-05-21
forum: Multimedia Software
---

### Post by cliff0108 on 2010-05-21
I have upgraded my Dell Dimension, dual boot from Breezy Badger to 10.04.
My mic no long works and the audio is terrible. When I boot back to XP the sound is all fine.
I gather the problem must be with the drivers installed for the sound card with 10.04 but am unsure what to do to correct this.
Any help appreciated.

---

### Post by lidex on 2010-05-21
Try this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo pulseaudio --kill
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

Next tweak mixer levels.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

---

### Post by cliff0108 on 2010-05-21
Thanks Lidex but when I enter:

sudo pulseaudio --kill
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf

in the termnal I get this :



cliff@cliff-desktop:~$ sudo pulseaudio --kill
[sudo] password for cliff: 
E: core-util.c: Home directory /home/cliff not ours.
E: main.c: Failed to kill daemon: Permission denied
cliff@cliff-desktop:~$ 

Is there a syntax error or did I do something wrong ?

Cliff

---

### Post by lidex on 2010-05-21
Just skip the first command and run the last two.
Haven't I seen you somewhere before? :rolleyes:

---

### Post by cliff0108 on 2010-05-21
When I try to run gnome-alsamixer in the run dialogue I get "could not locate the file."

Thanks for your continuing help :)

---

### Post by lidex on 2010-05-21
> **cliff0108 said:**
> When I try to run gnome-alsamixer in the run dialogue I get "could not locate the file."

Thanks for your continuing help :)

Probably doesn't come with the default install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by cliff0108 on 2010-05-22
I am making some progress with your help.
I installed alsamixer and appear to have adjusted the output levels satisfactorily so I get clear sound out of the speakers. both with mp3 and Cd music.
But I cannot yet get the mic to work.
I notice with alsamixer loaded there are two vertical slide bars for mic.
When I untick the mute on one the mic begins to broadcast through the speakers - so I definitely know it's working !
Problem is I can't seem to configure things to record, say, through "Sound Recorder" or Skype.
I note there are two selection boxes underneath the mic sliders "mute" and "rec" - but tried various combinations without success.
One other thing - and I don't know if it makes a difference - when I invoke "Sound Preferences/Input " the slider identifies the Analog Microphone as "unamplified" and I don't know if that makes a difference or how to change it.

---

### Post by waltercool on 2010-05-22
With alsamixer, press F4 and set CAPTURE and press Z (you must set left audio record as 0 and right audio record as 100)

Something like that: [http://i48.tinypic.com/315bi1y.png](http://i48.tinypic.com/315bi1y.png)

---

### Post by cliff0108 on 2010-05-22
Hummm
Great thought except that Capture brings up sliders for something called "3D Control"
Not 'mic'
I'm not sure how to include a screen capture of this in this reply..
I tried adjusting the 3D Control - but to no avail - and of course I don't really know what the heck I'm doing..  ;o)
I do appreciate the help I am getting and am becoming more3 confident we'll get this resolved.
cliff

---

### Post by lidex on 2010-05-22
In gnome-alsamixer, Use 'Edit -> Sound Card Properties' menu to enable elements. Try ticking/unticking elements there. Then use pulseaudio volume control (pavucontrol), the 'input devices' tab, to select the mic.

---

### Post by cliff0108 on 2010-05-23
"Then use pulseaudio volume control (pavucontrol), the 'input devices' tab, to select the mic."

Sorry.. I should know... but how do I invoke 'pavucontol' ?

---

### Post by lidex on 2010-05-23
If installed, it's in your 'Sound & Video' menu. Or Alt + F2 run dialog, enter 'pavucontrol'. To install:
```
sudo apt-get install pavucontrol paprefs pavumeter
```

---

### Post by cliff0108 on 2010-05-23
I installed this correctly now but while it shows the Pulse Audio Volume Meter for the Mic at it's max - left and right - there is no signal at all.
Not only that but the sound output which seemed to get better last night is back being crummy again - scratchy with much feedback.
Soewhere I read about a previous simpler sound system (previous to Alsa) and I wonder if I should put this on.
This is particularly upsetting because the sound is perfect when I boot to windows so I know it isn't the card, the hardware or the driver - it is the new Ubuntu.

---

### Post by lidex on 2010-05-23
A microphone is a mono device. You need to unlink the volume sliders and set one at zero. Feedback sound is probably sign of too much gain somewhere. Disable boost/amplifier options.

---

### Post by lidex on 2010-05-23
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by cliff0108 on 2010-05-23
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 1: CS46xx - Rear [CS46xx - Rear]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CS46xx [Sound Fusion CS46xx], device 3: CS46xx - Center LFE [CS46xx - Center LFE]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
cliff@cliff-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
cliff@cliff-desktop:~$ head -n 1 /proc/asound/card*/codec#*

---

### Post by cliff0108 on 2010-05-23
```

```
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 1: CS46xx - Rear [CS46xx - Rear]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CS46xx [Sound Fusion CS46xx], device 3: CS46xx - Center LFE [CS46xx - Center LFE]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
cliff@cliff-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
cliff@cliff-desktop:~$ head -n 1 /proc/asound/card*/codec#*

Dimension 4400 Desktop

---

### Post by cliff0108 on 2010-05-23
Dell dimension 4400 desktop

---

### Post by cliff0108 on 2010-05-23
I am having so many problems getting my sound to work properly.
What about Open Sound ? [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
Does anyone have any experience here.

I booted to Windows again and the sound is perfect there. I guess it's a matter of Ubuntu 10.04 not properly recognizing my soundcard. Weird, as I say, because the previous Breezy Badger had perfect sound as well - albeit, no webcam. (I did do a fresh install).

I love Ubuntu and would prefer it over Windows.
It's useless though if we have to re-boot every time for my wife to use Skype !

---

### Post by libertas on 2010-07-30
i had the same problem as you and searched the internet and found this solution that fixed my problem:

System>Preferences>Startup Applications

Click "Add"

Name: "Pulseadio daemon"

Command: "/usr/bin/pulseaudio"

Comment: "Start the sound daemon"

then restart your computer

Cheers :)

---

### Post by cliff0108 on 2010-07-31
Thanks - I shall give it a try !
c

---

### Post by lidex on 2010-07-31
Using the latest version of alsa may help. Try the alsa-upgrade link in my sig.

---

### Post by jango_0072003 on 2010-08-02
> **lidex said:**
> Using the latest version of alsa may help. Try the alsa-upgrade link in my sig.

This is bug in ubuntu 10.04. There is a work around for this. It worked  for me the work around is very simple. If you find that your sound card  are rest of the audio hardware are configured properly and the sound  still doesn't work do this:

[LEFT]1) Go to **System > Preferences > Startup Applications**
2) Press the **Add** Button
             Name:         **Pulseaudio daemon**
             Command:  **/usr/bin/pulseaudio**
             Comment:   **Start the sound daemon**
3) Now press the **Add** Button
4) Now Press the **Close** Button
5) Restart.

Your audio should be working now.
[/LEFT]

---

### Post by cliff0108 on 2010-08-05
Thanks - but neither solution works.
I have sound - but it is more often than not scratchy.
The mic doesn't work and I can't seem to get my Skype up and running.
I do believe I have tried most everything - but 10.04 seems incompatible with what I believe is my Turtle Beach Soundcard in a Dell Dimension.
The system is dual boot and of course everything is ducky in XP.
I love Linux though and wish I could get this working.
Perhaps the next release of Ubuntu.
I am always amazed and extremely grateful for all the help this community gives to one another !
Thank you,
Cliff

---

