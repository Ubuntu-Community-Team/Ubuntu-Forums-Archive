---
title: "2 USB Microphones in JACK - Assistance Needed"
date: 2017-08-10
forum: Multimedia Software
---

### Post by handydandyhim on 2017-08-10
Hello All,

I record a podcast with my wife using a Blue Yeti USB microphone and a Fifine USB microphone. Recently switched back to Linux due to some frustrations in the Windows space and I cannot figure out how to use JACK to route both of my microphones to a track in Audacity. I was using Voicemeeter Banana by VB-Audio in Windows to achieve this. I've read a few forum posts and blog articles about using JACK to route audio from different sound sources into a single application but I'm having problems setting it up.

Does anyone have a moment to help explain how to setup JACK to record and also monitor 2 USB mics or give a resource to point me in the right direction?

I appreciate any assistance!

---

### Post by Bucky Ball on 2017-08-10
Welcome. Bit like shooting in the dark without seeing the JACK 'Connections' tabs to see what you have there. Could you take a few screenshots (with each main entry in the Connections tabs 'opened' so we can see what's there) and post them, please?

Please attach the pics by hitting 'Adv Reply' for a new post and using the paperclip icon to upload (you can also use 'Go Advanced' if you are in 'Quick Reply') rather than inserting the pics into the body of the post. ;)

Hopefully, we can figure out what's going on and how to achieve what you want. Audacity, incidentally, also needs to have the input/output set correctly and JACK set, not ALSA (see drop-down menus in top left corner). Once that's set up right, try connecting Audacity to 'System' in the JACK Connections 'Audio' tab, if you see it there.

---

### Post by handydandyhim on 2017-08-10
Hey Bucky Ball,
Per your request I have uploaded a snapshot of my connection setup in JACK using qjackctl application.

I was able to figure out the setup in Audacity (I have previous experience in Windows with this application) and was able to get the input of my Yeti to pick up in Audacity but not the other mic.

Here is the list of my hardware using the *aplay -l* and *arecord -l* commands in Terminal.
```
nick@hdd-laptop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [USB PnP Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Microphone [Yeti Stereo Microphone], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
nick@hdd-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 1/1
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
card 2: Microphone [Yeti Stereo Microphone], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by Bucky Ball on 2017-08-11
All good, but are your actual USB mics shown in the ALSA tab of Connections?

---

### Post by handydandyhim on 2017-08-11
They are not shown. Please see attached screenshot.
Any thoughts?

---

### Post by handydandyhim on 2017-08-12
Due to different issues I was having I had to reinstall Ubuntu and JACK software.
I have updated the screenshot. I have also been digging elsewhere and I'm trying to make sense of using alsa-in/alsa-out to get the desired results but it is a bit over my head.

Here is a link to JACK Audio's instructions.
[http://jackaudio.org/faq/multiple_devices.html](http://jackaudio.org/faq/multiple_devices.html)

Any thoughts?

---

### Post by handydandyhim on 2017-08-14
So I have figured it out doing some additional sleuthing and taking my time to actually read the instructions on using the ALSA_IN command for the second mic.
***Note*** This only works for a second microphone. I don't think it will work with more because kicking off the alsa_in command a second time will stop the first instance of it running.

Step 1: Start JACK server (I use qjackctl)
Step 2: In the settings make microphone 1 the default input device.
Step 3: run alsa_in -j [name you wish to see for mic2] -d hw:[device from -arecord -l output] -q [quality of playback] 2>&1 1> /dev/null &
           example: alsa_in -j "Fifine" -d hw:Device -q 1 2>&1 1> /dev/null &
Step 4: Go to connections and map the new device to the system playback client
Step 5: Grab a cold IPA and marvel at what you've accomplished

```
nick@Handy-Ubuntu:~$ alsa_in -j "Fifine" -d hw:Device -q 1 2>&1 1> /dev/null &
[1] 14816
```

---

### Post by Bucky Ball on 2017-08-15
Excellent you have achieved a result and thanks for marking solved.

Unsure about your methods for getting there, but you got there. May I suggest you have a look at an app called 'Patchage' if you haven't already. It may make your life a little easier. It's in the official Ubuntu repos so easy to install. 

Good luck and enjoy. ;)

---

### Post by handydandyhim on 2017-08-15
Well, I didn't figure it out on my own. I found this resource from the "Penguin Producer". I'll check out Patchage, it came up frequently in my searches but I'm new to audio in Linux and I'm drinking from the fire hose right now.

[http://www.penguinproducer.com/Blog/2011/11/using-multiple-devices-with-jack/](http://www.penguinproducer.com/Blog/2011/11/using-multiple-devices-with-jack/)

---

### Post by handydandyhim on 2017-08-18
> May I suggest you have a look at an app called 'Patchage' if you haven't already.
After installing Patchage I noticed that it still requires the ALSA_IN command to run to view the additional input device. It doesn't pull in all available inputs, just the input that is maintained in the JACK setup. However, it is much nicer that the qjackctl connection manager. Thanks for the recommendation.

---

### Post by nik.charles on 2017-10-09
QjackCtl has options to run additional link commands and scripts.

In QjackCtl Settings, Options tab, enable the section "Execute script after startup" and put the alsa_in command for 2nd microphone in there

starting JACK will then automatically add the 2nd microphone

---

