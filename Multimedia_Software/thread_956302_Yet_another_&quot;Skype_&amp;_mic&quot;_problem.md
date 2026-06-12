---
title: "Yet another &quot;Skype &amp; mic&quot; problem"
date: 2008-10-23
forum: Multimedia Software
---

### Post by Calmatory on 2008-10-23
Well, I am aware that this has been discussed and solved numerous times before, heck, I've done that myself also. However, this time I have been unable to solve the problem or find a working solution, thus the thread.

Anyway, I am suspecting that this problem has something to do with Intrepid Ibex Beta. I know that one should expect this kind of problems and that no help is guaranteed just yet.

So, what does happen and what doesn't?

Facts:

aplay -l:
```
asdman@asdman-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

from lspci -v:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30d5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0580000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

With my current configuration I can hear the microphone from my speakers, thus I can assume that the microphone itself works. However, in Skype there is a feature to test the microphone and speakers with a sample call. My microphone fails as Skype doesn't record any sound from it.

I've toyed with various configurations for both Sound In and Sound Out options. "pulse" seems to work only for Sound Out and Ringing.

Available options:
```

Default device(Default)
HDA Intel (hw:Intel,0)
HDA Intel (plughw:Intel,0)
HDA Intel (hw:Intel,1)
HDA Intel (plughw:Intel,1)
hdmi
headset
pulse

```

When trying to do the sample call test with Default device(Default), I get an error which says "Problem with Audio Capture". Same happens with hdmi and headset. Others(HDAs and pulse) can't record the microphone.

What I suspect is the Volume Control(Alsa Mixer with GTK GUI?) can't unmute the devices under "Recording" for the Intel HDA. All the devices are muted. And will remain so if I close the window. It seems that the settings won't be saved, even though changing settings from "Playback" seem to work. I doubt this bug(?) was introduced with Intrepid Ibex beta I am using. Any workarounds for this?

I am more than eager to provide additional info, so don't hesitate to ask!

---

### Post by Calmatory on 2008-10-23
Anyone having any clues? Would love to have this sorted out before next monday. :(

---

### Post by lswest on 2008-10-23
I don't know for sure, since I don't use skype with a mic, but try checking out the info in this page: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)  I think the problem is that skype is trying to use the pulseaudio microphone, not the actual hardware microphone.  Follow the steps listed under "skype" in the above link and see if that helps.

---

### Post by kroetenmist on 2008-10-23
I do have the same problem with my Intel HDA chipset. Any solution ?

Bugreport : [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/288269](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/288269)

---

### Post by markbuntu on 2008-10-23
I have written a guide for using skype with pulseaudio. It is written for hardy but should also work with Intrepid, give it a try and let me know if it works or what you had to do to get it to work if it does not:

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

I have been having great difficulties getting Intrepid to work on my machine so I have been unable to try this myself. Hopefully my particular known hardware problems will be worked out by release date.

---

### Post by joris1977 on 2008-10-25
Ok I had the same problem after upgrading to Intrepid 8.10. How did I solve it?

Maybe it is good to follow this guide: [http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio+intrepid](http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio+intrepid)

but it might not be necessary,

I did it, but after that my MIC would still not work in skype. Really frustrating... 

What I did next?

Open up Pulse Audio device chooser to be found under -> Applications -> Sound & Video

Now there is on the panel a  new icon pulse audio icon: Click on it and there you can open Volume Meter (Recording) Try to speak through your MIC and watch if it registers any sound,the meter should go up a lot if you speak, if yes Pulse Audio is working. Than you problem is the skype settings. See down in this post.

If not, just as in my case. The volume meter didn't register my voice. Open up the Gnome volume control. It is the small speaker on your panel. You might have used it before to contol your sound. Click on it with the right mouse-button.  and select open volume control. 

In Gnome volume control: Device should be something similar to 'HDA Intel' (Alsa Mixer). Click on preferences and make sure all the tracks are visible. Make sure all of them are up and nothing is muted. Try if you have sound from your MIC on the Pulse audio volume meter.  

If not. Click on the next tab, probably something like 'recording' and do the same. 

If not. Check under options. In my case there were two Input sources. In my case Front MIC was selected. That looked good, because i was using the Front MIC, but really you should try the other options. Look at the Pulse Audio Volume meter if it registers any sounds. I am using the Front Mic, but when i changed it to MIC, i noticed The Pulse audio volume meter was registering my voice.:) 

If that works than the next step is to start skype. Go to options -> sound devices. Select for sound Out and for Ringing Pulse. For Sound in you choose one of the options that will look like, at least in my case, HDA Intel (hw:Intel,4) There are probably more options that look similar like this. Test them all with the skype test call. If the Pulse Audio Volume Recorder is registering your voice than there is probably a way to make skype work with your MIC.

If i write it down, it actually sounds not to difficult, but it wasn't, at least not for me. That's why anybody who claims that ubuntu is so nice, because it is so easy and intuitive to use should be punished by configuring skype in Intrepid. But at least i have got it working. Hope you can as well.

If not... skype sucks and is evil anyway so who cares...

And now i hope my girlfriend is going to call me soon from real far away....
;)

Hope this helps for anybody with a Mic problem and skype

---

### Post by jens83 on 2008-11-01
i would like to try, but i cant find "Pulse Audio device chooser" to be found under -> Applications -> Sound & Video

am i just stupid or is it not there? ive got intrepid btw
thanx

---

### Post by darkstaar on 2008-11-01
> **jens83 said:**
> ... i cant find "Pulse Audio device chooser" ...

am i just stupid or is it not there?

You'll probably have to install it. Search for 'padevchooser' in your package manager. You can install it from there.

---

### Post by aztechclan on 2008-11-01
I had a similar issue in Intrepid Ibex, however I did manage to solve it.  Double click the speaker icon to bring up the mixer.  Click preferences, enable all the options as follows "Microphone, MicBoost, Capture, Capture 1, Capture 2, Capture 3, IEC958, IEC958 Capture, IEC958 Default PCM.

Then, click un-mute for the Microphone.  Click the tab for 'Recording', move the capture volume up and 'toggle recording' also.

In skype audio settings, choose pulse for audio output and ring.  Choose one of the HDA Intel (hw:Intel,0) for Sound In (these devices are related to the 'Capture' devices in the mixer.

Hope that helps someone.  This is a macbook pro 3rd gen btw.

---

### Post by seekers on 2008-11-21
It works!  Thanks alot aztechclan..  I got the same gen of macbook.  Wow.

---

### Post by Sajmon75 on 2008-11-22
Great! It works for me too!!
Thanks Thanks Thanks Thanks!! :)

ps: my notebook is a poor acer.. :)

---

### Post by rajesh.kanakabandi on 2010-09-05
hi friend, 
i'm stuck with a strange problem. my mic records everything that is played via speakers but isn't recording my voice. can anyone tell me why this happens?

i've pulse audio installed. but the recording meter isn't going up very high.

both Ubuntu voice recorder and skype call test recorded music that i played on my system but not my voice.

please help.
thank you

---

