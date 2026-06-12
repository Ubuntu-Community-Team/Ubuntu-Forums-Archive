---
title: "No HDMI or Optical Out audio"
date: 2008-10-24
forum: Multimedia Software
---

### Post by Amorget on 2008-10-24
I have a Sony VGN AR-670 laptop with a nVidia 8700M GT and I don't seem to have any option at all for any sort of Digital Audio or HDMI.

aplay -l :

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

 cat /proc/asound/card0/codec#* | grep Codec :

```
Codec: SigmaTel CXD9872AKD
Codec: Conexant ID 2c06
Codec: Realtek ALC262

```

 lspci | grep -i audio :

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

I am running the nVidia 177.80 Video Drivers, but no HDMI being listed.

I am running ALSA 1.0.16 and the Linux -21_x64 kernel.

In the alsamixer is see this:

```
/proc/asound/devices:                                        #        &#9474;
&#9474;       &#9474;=====================                                        #        &#9474;
&#9474;       &#9474;  0: [ 0]   : control                                        #        &#9474;
&#9474;       &#9474;  1:        : sequencer                                      #        &#9474;
&#9474;       &#9474;  4: [ 0- 0]: hardware dependent                             #        &#9474;
&#9474;       &#9474;  5: [ 0- 1]: hardware dependent                             #        &#9474;
&#9474;       &#9474;  6: [ 0- 2]: hardware dependent                             #        &#9474;
&#9474;       &#9474; 16: [ 0- 0]: digital audio playback                         &#9618;        &#9474;
&#9474;       &#9474; 18: [ 0- 2]: digital audio playback                         &#9618;        &#9474;
&#9474;       &#9474; 24: [ 0- 0]: digital audio capture                          &#9618;        &#9474;
&#9474;       &#9474; 26: [ 0- 2]: digital audio capture                          &#9618;        &#9474;
&#9474;       &#9474; 33:        : timer    
```

But I don't see any of those digital audio playback options anywhere else.

Anyone have any ideas?

Douglas

---

### Post by superami on 2008-10-25
I have a very similar problem.  I have an MSI motherboard with an NVidia chipset that supports digital audio.

Here are my specs:

lspci | grep -i audio 
```
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
```

cat /proc/asound/devices
```
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 28: [ 0- 4]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 56: [ 1- 0]: digital audio capture
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

My system in running with the latest NVidia graphics driver from Envy and has an AMD64 X2 processor.

I would greatly appreciate any help in getting the sound to work, especially through the HDMI connector.

I have currently disabled pulse audio as well, as a possible fix to other sound problems I had had originally.

I have another minor annoyance at the moment, and that is flash audio often blocks other audio (like Skype) and vice versa, but I could live with that for now if I just had working support for digital output.

---

### Post by andyshedd on 2009-09-14
I got optical out working on my Vaio AR730E by following these steps:
(1) Download and install the Realtek Linux driver from here:
[http://www.realtek.com.tw/default.aspx](http://www.realtek.com.tw/default.aspx)
* In the "Quick Link" pane click "HD Audio Codec Driver"
(2) extract the archive and type "./install" in terminal as root from the extracted folder
(3) after that you need to configure "alsamixer"
* type "alsamixer" from terminal
* everywhere you see anything with "IEC958" that is listed as "MM" highlight it and type "M" to enable it. It should read 00 when enabled.
and finally (4) Open up Sound Preferences from "System>Preference>Sound" and enable "ALC262 Digital" in all the Sound Playback options. Of course you don't need to do all of them unless you want all to come out throught the optical digital port.
No clue on the HDMI functionality. I haven't gotten around to fixing that yet.
Sorry one last thing: I had to go back into alsamixer and mute all the outputs except the IEC958 ones.

---

### Post by Amorget on 2009-09-22
Holy crap, Andy, that worked perfectly!!  I finally have Digital Audio!!!  I tried it over the HDMI and it worked... amazing.  It's been a week now and I am still blown away every time I hook it up to the TV.

---

