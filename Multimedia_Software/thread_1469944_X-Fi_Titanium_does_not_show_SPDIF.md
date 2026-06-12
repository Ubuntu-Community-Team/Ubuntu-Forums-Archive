---
title: "X-Fi Titanium does not show SPDIF"
date: 2010-05-02
forum: Multimedia Software
---

### Post by Kleenux on 2010-05-02
Using latest Ubuntu 10.04, the Creative Sound Blater X-Fi Titanium does not show (sound preferences) SPDIF (Digital).

Only Analog options are present.

While ```
alsamixer
``` shows S/PDIF with max volume... (IN and OUT)


Is there any alsa-base "options" to configure to see SPDIF in Sound-preferences?

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Kleenux on 2010-05-02
I could get SPDIF OUT showing up in pavucontrol, but not SPDIF IN...
(for X-Fi)
```
# uname -a
Linux x.com 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```
```
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
```
```

# cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbff8000 irq 22
 1 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K2 SB0880


head -n 1 /proc/asound/card0/codec*
Codec: Realtek ALC888


# There is no 'codec' for X-Fi
# cat /proc/asound/card1/id
XFi
```

The PC is self-made, based on a Gigabyte GA-P55-ud3r motherboard.
Thanks for looking.

---

### Post by Kleenux on 2010-05-04
Btw I updated to Alsa 1.0.23.
alsamixer shows the SPDIF IN ok (and volume is set to max).

The question is : how to get the SPDIF IN to appear in applications?

---

### Post by Karail on 2010-05-04
I am getting the same problem. SPDIF is visible in alsamixer but digital output is not an option in the Sound Preferences dialog.

---

### Post by Kleenux on 2010-05-05
Let's open a club...

---

### Post by lidex on 2010-05-05
> **paris-unmatch said:**
> Btw I updated to Alsa 1.0.23.
alsamixer shows the SPDIF IN ok (and volume is set to max).

The question is : how to get the SPDIF IN to appear in applications?

What applications are you working with here? It may be more a matter of configuring the apps specifically.

---

### Post by Karail on 2010-05-05
> **paris-unmatch said:**
> Let's open a club...

Cool. What do you think we should call ourselves? :P

---

### Post by Kleenux on 2010-05-05
> **lidex said:**
> What applications are you working with here? It may be more a matter of configuring the apps specifically.

The need is to record SPDIF-IN.

SPDIF-IN appears in alsamixer, but not in the PulseAudio components (Sound Preferences, volume control, pavucontrol...).

Thus, the applications like SoundRecorder, Ardour get their input from PulseAudio and do not show SPDIF-IN.


> **Karail said:**
> Cool. What do you think we should call ourselves? 

The Expecting-Ubuntu-to-behave-like-a-mature-OS-and-provide-regular-Multimedia-out-of-the-Box-after-5.5-years-of-Existence club ?

---

### Post by Kleenux on 2010-05-06
Actually arecord -l is probably more relevant for SPDIF-IN
```
# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And an excerpt from Alsamixer for XFi / Capture```

    &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;   
    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
    &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;   
   L&#9492;&#9472;&#9472;&#9496;R      &#9492;&#9472;&#9472;&#9496;      L&#9492;&#9472;&#9472;&#9496;R     L&#9492;&#9472;&#9472;&#9496;R  
  CAPTURE    -------    CAPTURE    CAPTURE  
   80<>80    100<>100     0<>0     100<>100 
    PCM      Line-in      Mic     S/PDIF-in 

```S/PDIF is clearly shown in alsamixer, while no sign of it in arecord or Pulse.

What are the setting to set in .asoundrc to fix that? Thanks.

---

