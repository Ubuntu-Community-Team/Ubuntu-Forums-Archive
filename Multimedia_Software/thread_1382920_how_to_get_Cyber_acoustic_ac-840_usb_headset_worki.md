---
title: "how to get Cyber acoustic ac-840 usb headset working"
date: 2010-01-16
forum: Multimedia Software
---

### Post by cquigley on 2010-01-16
Hey Everyone-

  I know this topic has been covered and marked as solved, but I still cannot get this to work.

Here is the problem, I need to run Skype on my jaunty for work. My mic does not work with the mic in port on my acer aspire 5100 so I need a usb headset.

So I have the cyber acoustic ac-840 usb headset. How do I get the mic and headphones working? There is a post where I am suppose to go to /etc/modprobe.d/alsa-base.conf, I followed the instructions and nothing. Everything still comes through my speakers and no mic.

Now when I go into system>preferences>sound I get many options for usb setting, here they are below:

Under **Sound Events** my options are-
   USB Device 0xd8c:0x0c USB Audio (OSS)
   USB Device 0xd8c:0x0c USB Audio (OSS) ( I get this option twice, one work with 
                                                                  speakers the other with headphone)
   USB Device 0xd8c:0x0c USB Audio (ALSA) ( Iget a error message with this option)

Under **Music and Movies** I get the same options as above

Under **Audio Conferencing** I get the same as above for both Sound Playback and Sound Capture

Under **Default Mixer Tracks** I get:
   USB Device 0xd8c:0x0c (ALSA Mixer)
   Playback: USB Device 0xd8c:0x0c- USB Audio (PulseMixer)
   Capture: USB Device 0xd8c:0x0c- USB Audio (PulseMixer)

What is the difference between all these and which one do I select. 

Also when I click test I will get a sound in one of the "USB Device 0xd8c:0x0c USB Audio (OSS)" selections, however when I reboot it changes to "USB Device 0xd8c:0x0c USB Audio (OSS) (Not Connected)" what does this mean.

And Lastly when I'm in Volume Control I turn on the Microphone under the Playack tab and I get white noise coming from my built in computer microphone. And under the Recording tab I have control for "Capture" and "Capture 1" these are automatically set to off, I uncheck them and close Volume Control, however when I go back into Volume Control they automatically turn off again. 

I hope all this makes sense, I tried to add everything in, can someone please help me get thes going or I am going to have to revert to windows again.

Thanks,
   Chris

---

### Post by cquigley on 2010-01-16
Ok- I got the mic to work on the headset, and the test sound under System>Preferences>Soumd to woek on headphones. 

However, when I call someone through skype the sound still comes through the speakers and they can't here me but I can hear myself through the computer speakers.

Anyone know how to solve this?

thanks

---

### Post by frogotronic on 2012-05-16
> **cquigley said:**
> Ok- I got the mic to work on the headset, and the test sound under System>Preferences>Soumd to woek on headphones. 

However, when I call someone through skype the sound still comes through the speakers and they can't here me but I can hear myself through the computer speakers.

Anyone know how to solve this?

thanks

Under Sound Preferences, Choose Output, and select the "other" than the internal speakers => your sound should now be coming out through the headset speaker.

- CH

---

