---
title: "usb mic"
date: 2016-12-31
forum: Multimedia Software
---

### Post by mauricebis on 2016-12-31
I recently got a usb mic samson go mic which I got working through the pulse audio volume control choosing the samson option in the recording tab. I wanted to write a shell script that would take care of the configuration but I can't get it working, this is what i wrote bearing in mind that the usb mic is sound card 1 and the built-in audio 0:

[FONT=courier new]pulseaudio -k
pulseaudio --start

amixer -c 1 sset 'Mic',0 40%,40% unmute cap
amixer -c 0 sset 'Capture',0 mute nocap

echo "set-default-source alsa_input.usb-Samson_Technologies_Samson_GoMic-00-GoMic.analog-stereo" | pacmd 

ffmpeg  -f alsa  -ac 2 -ar 48000  -i pulse  -af volume=10   -acodec libmp3lame -y /home/maurice/tmp-maurice/capturedVideoAndSound.mp3 [/FONT]

But it doesn't work (ubuntu 12.04). Any idea as to what is missing ? Thanks.

---

### Post by TheFu on 2016-12-31
I have a Samson Go Mic too. Love it!

Find that the USB device moves around, so picking 1 device for a script by number wouldn't work for my system. I'd have to query the system for where that USB device was at the time.  I'd probably use lsusb and the udev device to find it.

Ubuntu 12.04 support ends in a few months. Time to move to the current LTS. I'd do that before dealing with this script.  There were lots of changes from 12.04 --> 16.04 and some of them change the way USB devices are handled.  Doing the migration now will be much easier than it is after support is gone.

---

### Post by mauricebis on 2017-01-01
OK for ubuntu 16.04 but this isn't really an answer to my question. The mic is well detected and the card number is n° 1 (the udev module of pulse does its job). The real question would be what are the sequence of commands pavucontrol generates to pulse/alsa when the proper option in the recording tab is selected since the mic works fine with pavucontrol.

---

### Post by TheFu on 2017-01-01
My point is that lots of things changed since 12.04. Moving to 16.04 first, THEN try to make it work would be smarter.
```

$ amixer -c 0 sset 'Capture',0 mute nocap
amixer: Unable to find simple control 'Capture',0
```

The pacmd input also fails.
```
echo "set-default-source alsa_input.usb-Samson_Technologies_Samson_GoMic-00-GoMic.analog-stereo" | pacmd 
Source alsa_input.usb-Samson_Technologies_Samson_GoMic-00-GoMic.analog-stereo does not exist.

```

So not working here as posted.  This worked:

```
echo "set-default-source alsa_input.usb-Samson_Technologies_Samson_GoMic-00.analog-stereo" | pacmd

``` Got it from the** pacmd list-sources  |grep alsa_input** cmd.

udev is part of systemd now. Don't know if that matters or not.
[https://askubuntu.com/questions/31206/how-can-my-audio-input-always-be-the-webcam-microphone](https://askubuntu.com/questions/31206/how-can-my-audio-input-always-be-the-webcam-microphone) says to set what you want in ~/.pulse/client.conf, but that it won't work since USB devices aren't seen when pulse starts up. They suggested a udev rule that gets invoked whenever the USB device is seen.  I like that idea.
 
Not important, but according to lsusb, have a 
Bus 001 Device 009: ID 17a0:0305 Samson Technologies Corp. GoMic compact condenser mic

Anyway, hope that link is helpful.

---

### Post by mauricebis on 2017-01-02
Thanks for your reply.
```

$ amixer -c 0 sset 'Capture',0 mute nocap
amixer: Unable to find simple control 'Capture',0
```

Fair enough but the card number is 1. (-c 1)

The pacmd input also fails.
```
echo "set-default-source alsa_input.usb-Samson_Technologies_Samson_GoMic-00-GoMic.analog-stereo" | pacmd 
Source alsa_input.usb-Samson_Technologies_Samson_GoMic-00-GoMic.analog-stereo does not exist.

```

This might be a diff between 12.04 and 16.04 for the name I have after listing sources is : alsa_input.usb-Samson_Technologies_Samson_GoMic-00-GoMic.analog-stereo

I  think that what would be needed is the right command (amixer/pacmd) to select the recording capture from the samson go mic ?

---

