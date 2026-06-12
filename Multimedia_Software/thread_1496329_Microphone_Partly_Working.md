---
title: "Microphone Partly Working"
date: 2010-05-29
forum: Multimedia Software
---

### Post by seshu6392 on 2010-05-29
I have a lenovo thinkpad and my internal microphone works only when i connect another mic through the jack.

Even the mic mute button present on my laptop is not working.

(There is no such problem on windows se7en)

Earlier, even an external mic never used to work. After some searching i added "options snd-hda-intel model = thinkpad" to my alsa-base.conf file. And then the **internal mic started working only when an external mic was connected**.

when i type "cat /proc/asound/card0/codec#* | grep Codec" i get:
Codec: Realtek ALC269
Codec: Intel G45 DEVCTG

I looked into the HD-Audio-Models.txt but couldn't locate the exact model for ALC269 so i searched online and decided to put model = thinkpad as i'd mentioned earlier.

But The alsa-mixer shows card to be HDA Intel and chp as intel g45 devctg.
Moreover, even this partial working of mic(s) is when i choose the input source in the alsamixer to be front mic and not int mic.

So I don't know what to do and am confused.
Please Help!

---

### Post by lidex on 2010-05-30
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by seshu6392 on 2010-05-30
Thank you for replying but it still isn't working...

I've attached a screenshot of pavu and the gnomemixer. Please correct me if I'm wrong.
The blue bar doesn't rise when i tap the mic or speak into it. I tried sound recorder, even that doesn't get it.

In the output devices port, i get to choose a port (speaker/headphone) but there's no such option in input devices..

One difference that i notice is that i now get a "chussshhhh" disturbance from my speaker..

Again, it works perfectly when i plug in an extnl mic.

Please continue to help :)

---

### Post by lidex on 2010-05-30
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

### Post by seshu6392 on 2010-05-30
```
seshan@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
seshan@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
seshan@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
seshan@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVCTG

```My laptop is Lenovo ThinkPad SL510.

---

### Post by seshu6392 on 2010-05-30
hey, meanwhile i just stumbled upon this thing:

[http://ubuntuforums.org/showthread.php?t=1350967&highlight=thinkpad+microphone](http://ubuntuforums.org/showthread.php?t=1350967&highlight=thinkpad+microphone)

What's your say about this? Do you think the links listed on that thread'll do it for me? (The status of that bug says incomplete)

---

### Post by lidex on 2010-05-30
Go for the alsa upgrade. Follow the alsa-upgrade link in my sig.

---

### Post by seshu6392 on 2010-05-30
I'll try the alsa upgrade script link and get back to you when i'm done. It'll be some time...

Thanks a lot in advance!

---

### Post by lidex on 2010-05-30
Before you do that remove the custom entry from alsa-base.conf

---

### Post by seshu6392 on 2010-05-30
Thanks a lot for that well-written link.

<bump>

The installation didn't complete.
```

***************************************************************************
*  alsa-utils-1.0.23 configure failed
***************************************************************************

```I've attached the log files. The download and compilation didn't report any error at the end.

So, what do I do now?

---

### Post by seshu6392 on 2010-05-30
Hey, but i just restarted my system and lo! its working!!!

Thanks a million :) you deserve a treat!

Cheers &
Enjoy

---

### Post by seshu6392 on 2010-05-30
hey! but guess what? i just restarted my comp and its working now :)

Thanks a lot :) you deserve a treat.

Cheers &
Enjoy

---

### Post by seshu6392 on 2010-05-30
hey! guess what... i just restarted the system and it worked!!!

thanks a lot :) you deserve a treat!!

Cheers &
Enjoy

---

### Post by seshu6392 on 2010-05-30
Well, now suppose i want to upgrade my 9.10 to 10.04, i dont want to be repeating all this. Plus, i have lots of libraries installed like avr-gcc, libserial, urg, openCV etc... so i dont want to ./configure; make and sudo make install each one all over again.

So if i upgrade, will all these be lost?

details: [http://ubuntuforums.org/showthread.php?t=1497015](http://ubuntuforums.org/showthread.php?t=1497015)

---

### Post by lidex on 2010-05-30
Make sure this file is installed:
```
sudo apt-get install libncurses5
```

---

### Post by seshu6392 on 2010-05-30
er... what is this for?

---

### Post by brandon.barista on 2010-06-07
Sound has been fussy ever since upgrade to 10.04 have done a fresh install (again) for both alsa and pulse, still no progress with audio in skype or getting pulse to see my hardware. Also I have to change my alsa settings every login.

```
$ uname -a
Linux a-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP)
~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC272

```

---

### Post by lidex on 2010-06-07
> **brandon.barista said:**
> Sound has been fussy ever since upgrade to 10.04 have done a fresh install (again) for both alsa and pulse, still no progress with audio in skype or getting pulse to see my hardware. Also I have to change my alsa settings every login.

```
$ uname -a
Linux a-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP)
~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC272

```

Try this:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

No help? Use the alsa-upgrade link in my sig to get v 1.0.23

What is the make/model of this laptop?

---

