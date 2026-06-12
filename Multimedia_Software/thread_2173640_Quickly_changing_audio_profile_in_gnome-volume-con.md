---
title: "Quickly changing audio profile in gnome-volume-control?"
date: 2013-09-10
forum: Multimedia Software
---

### Post by jeremy4 on 2013-09-10
I'm hoping somebody here has encountered this issue and can assist.  

I have a Dell XPS 14Z laptop with Integrated HD 3000 chipset,  and the sound works great on the internal speakers.  I can also change to HDMI audio output  by going into gnome-volume-control, going to Hardware tab, and then choosing the "Digital Stereo (HDMI) Ouput" option.  However, this is not very efficient for changing the audio output on the fly.  Here is a screenshot of of my audio device in gnome-volume-control:

[[IMG]http://i13.photobucket.com/albums/a262/jsgates/sound_profile.png[/IMG]](http://s13.photobucket.com/user/jsgates/media/sound_profile.png.html)

As you can see this only shows up as one audio device, and changing the Profile changes the output from internal speakers to HDMI and vice versa.  I am looking for a way to change the profile (bash script possibly) with a single click, so that I can easily toggle between the laptop speakers, and HDMI out to the TV.  

Running aplay -l from the terminal returns:

```

[COLOR=#2E8B57][FONT=Monaco]default[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Playback/recording through the PulseAudio sound server[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]sysdefault:CARD=PCH[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Default Audio Device[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]front:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Front speakers[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]surround40:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    4.0 Surround output to Front and Rear speakers[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]surround41:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    4.1 Surround output to Front, Rear and Subwoofer speakers[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]surround50:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    5.0 Surround output to Front, Center and Rear speakers[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]surround51:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    5.1 Surround output to Front, Center, Rear and Subwoofer speakers[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]surround71:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]hdmi:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 2805 Digital[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDMI Audio Output[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]dmix:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Direct sample mixing device[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]dmix:CARD=PCH,DEV=3[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 2805 Digital[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Direct sample mixing device[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]dsnoop:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Direct sample snooping device[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]dsnoop:CARD=PCH,DEV=3[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 2805 Digital[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Direct sample snooping device[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]hw:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Direct hardware device without any conversions[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]hw:CARD=PCH,DEV=3[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 2805 Digital[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Direct hardware device without any conversions[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]plughw:CARD=PCH,DEV=0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 269 Analog[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Hardware device with all software conversions[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]plughw:CARD=PCH,DEV=3[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    HDA Intel PCH, ID 2805 Digital[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]    Hardware device with all software conversions

```[/FONT][/COLOR]

& aplay -L returns:

```

[COLOR=#2E8B57][FONT=Monaco]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]card 0: PCH [HDA Intel PCH], device 0: ID 269 Analog [ID 269 Analog][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]card 0: PCH [HDA Intel PCH], device 3: ID 2805 Digital [ID 2805 Digital][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]  Subdevice #0: subdevice #0
[/FONT][/COLOR]
```

Any help resolving this minor issue is much appreciated.

-hogfan

---

