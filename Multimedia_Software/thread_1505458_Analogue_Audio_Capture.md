---
title: "Analogue Audio Capture?"
date: 2010-06-09
forum: Multimedia Software
---

### Post by Jake007g on 2010-06-09
First off, I'd like to say please excuse my poor terminology, I'm a slight noob in this field :-)

Anyway, so I've got an easyCAP analogue capture device. It has three component cables (Red, white and yellow) on one end, and USB on the other end.

I've managed to install some video drivers and make a menCODER script to get the video to record perfectly. Now, I need some assistance in getting the audio to record. I haven't (and not sure if I need to) installed any audio drivers.

This is the current menCODER script I'm using, which only records video (And a buzzing/hissing audio sound):

> mencoder tv:// -tv driver=v4l2:width=720:height=480:device=/dev/video0:forceaudio:adevice=/dev/dsp:immediatemode=0:audiorate=44100:input=1:norm=PAL-60 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000:aspect=16/9 -oac mp3lame -lameopts mode=2 -o Recording

I also tried ALSA inputs at one point:
> mencoder tv:// -tv driver=v4l2:width=720:height=480:device=/dev/video0:forceaudio:alsa:adevice=hw.1:immediatemode=0:audiorate=44100:input=1:norm=PAL-60 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000:aspect=16/9 -oac mp3lame -lameopts mode=2 -o Recording


I have absolutely no idea how to get the audio to record. 

ANY help what so ever will be greatly appreciated

-Jake

---

### Post by cchhrriiss121212 on 2010-06-09
Try putting arecord -l into a terminal, which will show you what (if any) recording devices ALSA recognises. If it is not recognised then I doubt it is supported.

---

### Post by Jake007g on 2010-06-09
> **cchhrriiss121212 said:**
> Try putting arecord -l into a terminal, which will show you what (if any) recording devices ALSA recognises. If it is not recognised then I doubt it is supported.

Thank you for the help, this is the output I got:
> **** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0xeb1a0x2861 [USB Device 0xeb1a:0x2861], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



I'm very certain that
> card 1: U0xeb1a0x2861 [USB Device 0xeb1a:0x2861], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Is my easyCAP, where do I go from here? :)

Thanks for your help so far, I appreciate it :D

EDIT: That is definitely my easyCAP, when I unplugged it and re entered that into the terminal that device disappeared, and then when I plugged it in again it came back up.

---

### Post by cchhrriiss121212 on 2010-06-09
Thats good news, next put alsamixer in a terminal hit f4 and select the USB device. Then set the capture levels as they are likely at a low amount.

---

### Post by Jake007g on 2010-06-09
Ok, done that now, one of them was on minimum. What audio device do I put in menCODER now, is it alsa:hw.1,0: ? Or do I need to do something else before?

PS, thank you very much for taking your time to help me :-)

---

### Post by cchhrriiss121212 on 2010-06-10
I'm not too familiar with mencoder, but judging from you arecord -l output I would say that hw:1/hw:1,0 is a good place to try. You could try testing it with something simple like audacity if it does not go right.

---

### Post by Jake007g on 2010-06-11
hw.1 and hw.1,0 didn't work, also, when when hw:1,0 is selected as the recording device in audacity, there is no audio. :S

---

### Post by cchhrriiss121212 on 2010-06-11
Are you using ALSA or pulse when you try with Audacity?
Do you need to capture the audio and video at the same time, or are you going to do them separately and then sync them with some video editor?

---

### Post by Jake007g on 2010-06-11
> **cchhrriiss121212 said:**
> Are you using ALSA or pulse when you try with Audacity?
Do you need to capture the audio and video at the same time, or are you going to do them separately and then sync them with some video editor?

I've only tried ALSA in audacity, I'll give pulse a try now and let you know the results...

And, I could do with recording them both at the same time as it's easier, but if I can only do them separate and sync them I s'pose it'l do :)

Cheers <3

---

### Post by Jake007g on 2010-06-11
Pulse didn't do anything. I've been playing around with A LOT of settings in preferences>sound, like the input etc, I've set it to analogue, but I really don't know what I'm doing if I'm honest xD

---

### Post by cchhrriiss121212 on 2010-06-12
ALSA should always give you better results than pulse. Would you be able to use the onboard audio to record sound while using the easycap for video?

---

### Post by Jake007g on 2010-06-12
> **cchhrriiss121212 said:**
> ALSA should always give you better results than pulse. Would you be able to use the onboard audio to record sound while using the easycap for video?

Not really sure, how would I go about trying? Sorry I'm a noob xD

---

### Post by cchhrriiss121212 on 2010-06-12
Plug in the audio cables (white and red) from your video source into your computer jack and try using it (hw:0,0 from your earlier arecord -l) with audacity or something. You would need an adapter to use both cables, but you can test it with just one.

---

### Post by Jake007g on 2010-06-13
That didn't do much, didn't even get a fuzzy output, just no sound :/

---

### Post by cchhrriiss121212 on 2010-06-13
Did you connect it to the correct input jack? You want the one that has a mic symbol or is coloured red. Did you also check that the levels were OK in alsamixer?

---

### Post by Jake007g on 2010-06-13
Yep, I tried with both red and white analogue audio cables, and I plugged them intro my mic jack. I double checked the audio levels were adequate in alsamixer, and I also tried recording all of my hw: devices in audacity, but no luck :/

EDIT: Don't know if this means anything..
> [  228.748630] easycap: easycap_module_init: ========easycap=======
[  228.748636] easycap: easycap_module_init: version: 0.7.1
[  228.748687] usbcore: registered new interface driver easycap
[  270.180027] usb 1-3: new high speed USB device using ehci_hcd and address 6
[  270.312522] usb 1-3: configuration #1 chosen from 1 choice
[  270.336946] Linux video capture interface: v2.00
[  270.345977] em28xx: New device @ 480 Mbps (eb1a:2861, interface 0, class 0)
[  270.346112] em28xx #0: chip ID is em2860
[  270.436494] em28xx #0: board has no eeprom
[  270.448997] em28xx #0: Identified as Unknown EM2750/28xx video grabber (card=1)
[  270.459371] em28xx #0: found i2c device @ 0x4a [saa7113h]
[  270.482623] em28xx #0: Your board has no unique USB ID.
[  270.482628] em28xx #0: A hint were successfully done, based on i2c devicelist hash.
[  270.482632] em28xx #0: This method is not 100% failproof.
[  270.482635] em28xx #0: If the board were missdetected, please email this log to:
[  270.482639] em28xx #0: 	V4L Mailing List  <linux-media@vger.kernel.org>
[  270.482643] em28xx #0: Board detected as EM2860/SAA711X Reference Design
[  270.482647] em28xx #0: Registering snapshot button...
[  270.482737] input: em28xx snapshot button as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/input/input6
[  270.848414] saa7115 0-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[  271.564234] em28xx #0: Config register raw data: 0x10
[  271.588112] em28xx #0: AC97 vendor ID = 0x414c4760
[  271.600118] em28xx #0: AC97 features = 0x0000
[  271.600123] em28xx #0: Unknown AC97 audio processor detected!
[  272.060028] em28xx #0: v4l2 driver version 0.1.2
[  272.988190] em28xx #0: V4L2 video device registered as /dev/video0
[  272.988195] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[  272.988399] em28xx audio device (eb1a:2861): interface 1, class 1
[  272.988434] em28xx audio device (eb1a:2861): interface 2, class 1
[  272.988473] usbcore: registered new interface driver em28xx
[  272.988478] em28xx driver loaded
[  273.010002] usbcore: registered new interface driver snd-usb-audio
[  292.450372] usb 1-3: USB disconnect, address 6
[  292.450500] em28xx #0: disconnecting em28xx #0 video
[  292.450504] em28xx #0: Deregistering snapshot button
[  292.480147] em28xx #0: V4L2 device /dev/vbi0 deregistered
[  292.480253] em28xx #0: V4L2 device /dev/video0 deregistered
[  297.448025] usb 1-3: new high speed USB device using ehci_hcd and address 7
[  297.580509] usb 1-3: configuration #1 chosen from 1 choice
[  297.580672] em28xx: New device @ 480 Mbps (eb1a:2861, interface 0, class 0)
[  297.580755] em28xx #0: chip ID is em2860
[  297.672662] em28xx #0: board has no eeprom
[  297.684367] em28xx #0: Identified as Unknown EM2750/28xx video grabber (card=1)
[  297.694366] em28xx #0: found i2c device @ 0x4a [saa7113h]
[  297.717744] em28xx #0: Your board has no unique USB ID.
[  297.717749] em28xx #0: A hint were successfully done, based on i2c devicelist hash.
[  297.717753] em28xx #0: This method is not 100% failproof.
[  297.717756] em28xx #0: If the board were missdetected, please email this log to:
[  297.717760] em28xx #0: 	V4L Mailing List  <linux-media@vger.kernel.org>
[  297.717763] em28xx #0: Board detected as EM2860/SAA711X Reference Design
[  297.717768] em28xx #0: Registering snapshot button...
[  297.717857] input: em28xx snapshot button as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/input/input7
[  298.080909] saa7115 0-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[  298.788234] em28xx #0: Config register raw data: 0x10
[  298.812229] em28xx #0: AC97 vendor ID = 0x414c4760
[  298.824106] em28xx #0: AC97 features = 0x0000
[  298.824110] em28xx #0: Unknown AC97 audio processor detected!
[  299.284022] em28xx #0: v4l2 driver version 0.1.2
[  300.212200] em28xx #0: V4L2 video device registered as /dev/video0
[  300.212205] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[  300.212289] em28xx audio device (eb1a:2861): interface 1, class 1


---

### Post by Jake007g on 2010-06-13
Update:

Been playing around for a few hours now, and with my red audio component cable plugged into my front mic, I've managed to get an output from hw:0,0 in audacity. Albeit, very amplified, but at least we're getting somewhere :-)

What shall I do next?

Thank you very much for all your help so far! :D

---

### Post by cchhrriiss121212 on 2010-06-14
Well if you are happy using the front mic then just get one of [these]("http://cgi.ebay.co.uk/3-5mm-Stereo-Jack-2-x-RCA-Phono-Left-Right-Audio-/290440198095?cmd=ViewItem&pt=UK_AudioVisualElectronics_PortableAudio_MP3PlayerSpeakers&hash=item439f95b7cf"). Then the sound quality will be better. When you say amplified, do you mean it is too loud or is it distorted?

---

### Post by Jake007g on 2010-06-14
> **cchhrriiss121212 said:**
> Well if you are happy using the front mic then just get one of [these]("http://cgi.ebay.co.uk/3-5mm-Stereo-Jack-2-x-RCA-Phono-Left-Right-Audio-/290440198095?cmd=ViewItem&pt=UK_AudioVisualElectronics_PortableAudio_MP3PlayerSpeakers&hash=item439f95b7cf"). Then the sound quality will be better. When you say amplified, do you mean it is too loud or is it distorted?

When I said amplified, it sounded alien like. I turned the levels down in alsamixer though, they sound great now. 

I've also got something which does the same as that item, I've attached an image of how I've got it set up :-D

Here is a video sampling the video&sound:
[http://www.youtube.com/watch?v=pU73xsyX-eg](http://www.youtube.com/watch?v=pU73xsyX-eg)

Thank you very much for all of your help, I really do appreciate it. The support from friendly people like you is what makes Linux such a great experience!

---

### Post by CJ_Hudson on 2010-06-17
Hiya, I've got similar problems with Audacity.
Tried it on Windows, could hear something from the input, but on Ubuntu nothing, it's just dead and refuses to record.

Hey, I got it working. Try this thread:

[http://ubuntuforums.org/archive/index.php/t-505103.html](http://ubuntuforums.org/archive/index.php/t-505103.html)

---

### Post by CJ_Hudson on 2010-06-30
Hey, have you tried Audacity? It's brilliant, it took a bit of tweaking to get the input selected but works a treat now!

---

