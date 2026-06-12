---
title: "usb Webcam as a default audio input device?"
date: 2010-10-15
forum: Multimedia Software
---

### Post by pjotruk on 2010-10-15
Hi, 
I'm having here annoying "problem" with my webcamera. Everytime I want to use it as a microphone it needs to be switched manually in sound settings menu. It's not a big deal but I would really rather let it be switched automatically like plug and play or something like that. Any ideas how to do it, where to do it? thanks

ubuntu 10.10
Intel ICH6

---

### Post by riseringseeker on 2010-10-17
I would love to hear if there is a way to set an external input device as the default.  I use a webcam/microphone, (logitech 9000 pro) and always have to select it after it is plugged in (won't use it automagically even when plugged in before power on).  Would love to have the system recognize it as the default.  Have a friend who would like the same functionality with his bluetooth headset.

Please, anyone know how this can be accpmplished?

---

### Post by Bolick on 2011-01-11
I have just the same problem. USB webcam's microphone selected as input in "Sound preferences" becomes inactive after reboot and motherboard's analog input becomes active. That causes problems each time I use Skype after reboot.

---

### Post by rzach on 2011-01-17
First go to audio settings and select you webcam microphone as the input device. Then:

# pacmd
>>> dump

will give you the configuration of your pulseaudio daemon.  One of the last lines will be something like this:

set-default-source alsa_input.usb-046d_0809_CCE11299-02-U0x46d0x809.analog-mono

Add that line to the end of your /etc/pulse/default.pa file

This seems to work for me, but note that pulseaudio will lose the USB webcam mic every time the USB connection shuts down. So, eg, if your webcam is plugged into the USB hub on your monitor and the monitor goes to sleep, disconnecting the webcam, pulseaudio will switch to the internal audio input. Don't know how to fix that.  There's a bug report in launchpad:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640328](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640328)

---

### Post by Ubiquitine on 2011-01-18
> **rzach said:**
> First go to audio settings and select you webcam microphone as the input device. Then:

# pacmd
>>> dump

will give you the configuration of your pulseaudio daemon.  One of the last lines will be something like this:

set-default-source alsa_input.usb-046d_0809_CCE11299-02-U0x46d0x809.analog-mono

Add that line to the end of your /etc/pulse/default.pa file

This seems to work for me, but note that pulseaudio will lose the USB webcam mic every time the USB connection shuts down. So, eg, if your webcam is plugged into the USB hub on your monitor and the monitor goes to sleep, disconnecting the webcam, pulseaudio will switch to the internal audio input. Don't know how to fix that.  There's a bug report in launchpad:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640328](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640328)
Thank you a lot. Really helpful.

---

### Post by Bolick on 2011-01-18
rzach thanks a lot, I'll give it a try

---

### Post by kbenoit on 2011-02-14
Thanks a lot for the tip, I made a script called by udev when my QuickCam get plugged to switch the input-source in pulse-audio. It is ugly, but works for now.

So I created /etc/udev/rules.d/97-QuickCam_E2500.rules
```
SUBSYSTEM=="usb", ACTION=="add", ATTR{idVendor}=="046d", ATTR{idProduct}=="089d", RUN+="/usr/local/bin/QuickCam_E2500_hotplug.sh"
```

Then /usr/local/bin/QuickCam_E2500_hotplug.sh
```
#!/bin/bash
delegate=`dirname $0`/QuickCam_E2500_hotplug_delegate.sh

$delegate &
```

Since I could'nt find how to get called after pulseaudio was updated, I had to create the following delegate that tries every second for 5 seconds. So the file /usr/local/bin/QuickCam_E2500_hotplug_delegate.sh contains:
```
#!/bin/bash
#Configure this as your home directory
export HOME=/home/#Your username
#Configure this as your username. If you have multiple user on your computer, you'll have to adapt this script.
pulseaudio_user=#Your username
#Those are the vendor and product id of your usb device, as found in:
# udevadm info --attribute-walk --path=/sys/devices/pci0000\:00/0000\:00\:1d.1/usb3/3-1/input/input12/
# look at the output of dmesg to find the right path. Those numbers are also found directly in dmesg:
# ...
# gspca: probing 046d:089d
# ...
# and in the pulse audio card name eg: usb-046d_089d-01-U0x46d0x89d. In fact we only match the pulseaudio
# card name. 
idvendor="046d"
idproduct="089d"

# poll pulseaudio for the newly plugged card.
counter=0
while [ $counter -lt 5 ] ; do
  srcname=`sudo -u $pulseaudio_user pacmd dump | grep "set-card-profile.*$idvendor.*$idproduct.*input" | sed -ne 's/.*\.\([^ ]*\) input:\(.*\)/alsa_input.\1.\2/p'`
  if [ ! -e $srcname ] ; then
    break
  fi
  sleep 1
  let counter=counter+1
done

# Set it as the default source.
if [ ! -e $srcname ] ; then
  sudo -u $pulseaudio_user pacmd set-default-source $srcname
fi
```

---

### Post by mondeoscotch on 2011-03-05
I have tried rzach way but it didn't worked for me :-( whereas kbenoit scripts are working very well \\:D/ , thank you so much  :-)

---

### Post by craq on 2011-04-22
thanks! this worked for me too. With the proviso that the scripts have to be set executable.

There are a few ways to find out the vendor id and product id which you need to change in the udev rule and the delegate script. 

```
$ pactl list

```
gives all the information you need, with labels

```
$ lsusb
Bus 001 Device 005: ID 046d:0805 Logitech, Inc.
```
doesn't fill your screen as much. Here 046d is the vendor id and 0805 is the product id

```
pacmd dump | grep usb
```
gives more information again. The vendor and product ids come directly after usb- and in that order

---

### Post by Bryan55 on 2012-03-06
I have found a way around this problem.
Go to Sound settings and select "Hardware" tab. Highlight Internal Audio. Then in the Profile field select "Analogue Stereo Output". You should then find in the "Input" tab there is only the webcam to chose from. So it will be selected every time.
If you use any other microphones this is not a solution for you.

Bryan

---

### Post by farmer_donny on 2012-03-11
Thankyou Bryan55
Your way is elegant, it works andis probably the way the programmers intended it to be set up.

---

### Post by Bryan55 on 2012-06-16
Unfortunately my work around is not possible in 12.04

Bryan

---

### Post by dominator1 on 2012-08-29
if you use wine you can use wine configuration editor audio tab audio input to select any attached microphone including on board and usb can change as desired:guitar:

---

