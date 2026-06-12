---
title: "Analog audio not working in some apps"
date: 2011-04-25
forum: Multimedia Software
---

### Post by tomtuttle on 2011-04-25
I am quite new to ubuntu, and am trying very hard to solve my own problems.  The generosity of the user community is astounding.

I have a Zotac Zbox HD-11.  It is running ubuntu 10.04.  Primary intended use for the machine is a media client. It is attached via both SPDIF and analog (headphone) to an Onkyo TX-SR805 receiver.  I need BOTH the digital and analog so that I have high quality DAC via the optical and can route the signal to Zone2 and Zone3 from the analog input.

My problem is that the analog output does not seem to work on Rhythmbox or Banshee BUT I do get both the digital and analog signals when using system sounds, streaming through Chrome and using Audacity.

This makes no sense to me.

I ran the diagnostic suggested in another thread and the results are here:

[http://www.alsa-project.org/db/?f=0cd3f3b5470bcc0c6f4580db12d86948e3dd3cd1](http://www.alsa-project.org/db/?f=0cd3f3b5470bcc0c6f4580db12d86948e3dd3cd1)

Now, I did perform several operations in alsa and updated the kernel in order to try and get audio via HDMI.  Ultimately, I abandoned the idea of audio via HDMI for reasons more due to cabling and other devices, but it is possible (if not likely) that I messed something up along the way.

I've been chasing this for a long time, and am stumped.

I will need very basic instructions on remediation, as I am not yet very savvy with linux.

Any guidance very sincerely appreciated.

---

### Post by tomtuttle on 2011-04-25
Bump?  :)

---

### Post by KegHead on 2011-04-25
Hi!

Real basic:

system...preferences...sound..output.

Change to analog headphones?

Keghead

---

### Post by tomtuttle on 2011-04-26
Thank you for trying to help me; I do appreciate it.

When I look in System - Preferences - Sound, I do not have those choices.

I have instead:

Internal Audio Analog Stereo (this is checked)
High Definition Audio Controller Digital Stereo (HDMI)

I am NOT using the HDMI (Nvidia) controller.

Also, I am trying to get SIMULTANEOUS output from the TOSLINK and the headphone jack.  I do get this  with the system and browser, but not with the music streaming applications.

---

### Post by tomtuttle on 2011-04-26
Do some applications call the default (system) sound profile in different ways than others?

Any help?

---

### Post by lidex on 2011-04-27
> **tomtuttle said:**
> Do some applications call the default (system) sound profile in different ways than others?

Any help?
Yes they do. Run this in terminal:
```
gstreamer-properties

```
and try some different values.

---

### Post by Yellow Pasque on 2011-04-27
> **tomtuttle said:**
> Do some applications call the default (system) sound profile in different ways than others?


The programs you listed as working (system sounds via libcanberra, Flash, Audacity) all use ALSA libs directly, so I'm guessing this is an issue with pulseaudio.

---

### Post by lidex on 2011-04-27
Perhaps this then:
> Simultaneous Output

In the PA Device Chooser/Configure Local Sound Server/Simultaneous Output there is a check box for Simultaneous Output to all local sound cards. If you select it this will add a new Output Device in the PA Volume Control listings
Simultaneous output to ALSA PCM.......(all your sound hardware devices).......
You can select this device in the PA Volume Control just like any other and it will direct streams to all your sound devices simultaneously so you can have sound in your speakers and usb headset etc at the same time.

You'll need pulse audio preferences in the 'System > Preferences' menu. If not installed:
```
sudo apt-get install paprefs pavucontrol
```

---

### Post by tomtuttle on 2011-04-27
Thank you both so much!  I will test these approaches and report back.

---

### Post by tomtuttle on 2011-04-29
Checking the simultaneous output box seems to have worked!  Wonderful!  Thank you so much!

---

### Post by lidex on 2011-05-01
If all is good, please mark the thread solved using 'Thread Tools' up top.

---

