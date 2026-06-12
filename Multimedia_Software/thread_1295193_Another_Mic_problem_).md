---
title: "Another Mic problem :)"
date: 2009-10-19
forum: Multimedia Software
---

### Post by karimruan on 2009-10-19
I did my research, and couldn't get it working, but I found this:
"""
If your microphone does not seem to be working Open the Volume Control from your panel ( the little speaker icon) and check that it is set to the proper device (your hardware). Click Preferences and make sure that the boxes for Microphone Capture and Mic Boost Capture are checked, close the box. In the Volume Control/ Switches check the Mic Boost Capture box. In /Recording make sure the Microphone is not muted (no red x on the mic icon) and turned up. (Some devices do not have a mic boost option)

Try recording again. If it still does not work check for any other mic switches or controls and play around with them.

Remember, it is the capture/recording settings that are important for recording. Playback settings get your mic to your speakers.

If you are still having problems with your mic it is most likely a problem with the alsa driver. This is a very common issue for laptop users and fixes are very hardware specific. You should search the forums or google for your specific make and model of machine for a solution.
"""

I don't really see any mic switches, no mic boost option, and i am running jaunty, which the article said it was for. I don't touch the hardware on laptops, so I refuse to change anything, but I do think it is just a driver issue. I do not know much about mics or speakers and how they work, so i am coming here. Do mics use drivers? Or are they integrated with another hardware component, whose driver isn't fully working in Ubuntu for me? I have found MANY others who have had similar problems, but mainly only when using skype. I don't use skype and I need my mic to make presentations for my business. I do not regret moving to ubuntu, I just wish I could get EVERY little thing on my system working!


EDIT:

My lappy is an HP DV6700
AMD TURION64 x2 CPU
Nvidia (not sure what card I am using)
Don't know about my sound card.

---

### Post by karimruan on 2009-10-19
Just an update, my mic is not muted, all other sound related stuff works fine. Is there any hope for me?

EDIT:

Using aplay -l I got this input:

mat@mat-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mat@mat-laptop:~$

---

