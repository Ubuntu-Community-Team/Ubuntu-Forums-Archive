---
title: "USB Sound Card Configuration (Ubuntu - 8.04)"
date: 2009-01-28
forum: Multimedia Software
---

### Post by raghuvarrier on 2009-01-28
Hi

Am using ubuntu 8.04 on my laptop with following configuration

HP Compaq nx 6125
Turion ML-30 Processor
1.5 gb RAM

I recently purchased a 5.1 channel usb audio card, make  C-Media Electronics, Inc. Music2go. The card was detected in ubuntu, but am not able to configure it for 5.1 channel output. The output of 'lsusb' and 'aplay -l' are as follows

~$lsusb
Bus 003 Device 004: ID 13fd:1040  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0d8c:0006 C-Media Electronics, Inc. 
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 15d9:0a4c  
Bus 001 Device 001: ID 0000:0000  

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any help is highly appreciated, Thanks in advance

---

### Post by billt1 on 2009-01-29
Hi, I don't have a solution, but do have a question.

My on board sound card died and I'm thinking of replacing it.  Does your USB sound card work in any mode (stereo vs. 5.1)????

Thanks

---

### Post by raghuvarrier on 2009-01-31
yea it works in stereo mode. you have to change the sound output devices to "usb audio" in sound preferences tab. same you may have to repeat for your audio and video player audio output plugins

---

### Post by kostkon on 2009-01-31
*raghuvarrier* check [this thread]("http://ubuntuforums.org/showthread.php?t=789578") to better setup *PulseAudio* in 8.04 (because in *Hardy*, *PulseAudio* is not setup the right way) and then [this thread]("http://ubuntuforums.org/showthread.php?t=795525") to enable 5.1.

Hope that helps.

---

### Post by raghuvarrier on 2009-02-04
Thank you kostkon for your help

---

### Post by raghuvarrier on 2009-02-06
kostkon following the instructions in the link provided did not solve my problem

---

