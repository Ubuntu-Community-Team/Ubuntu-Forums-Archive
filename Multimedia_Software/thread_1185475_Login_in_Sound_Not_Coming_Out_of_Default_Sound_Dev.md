---
title: "Login in Sound Not Coming Out of Default Sound Device"
date: 2009-06-12
forum: Multimedia Software
---

### Post by ptorpey on 2009-06-12
I have two external USB sound devices hooked up to my system.
I amusing Ubuntu 9.04.

In the System / Preferences / Default Sound Device, I selected to use my SB-Live device.

When I restart the computer, here is what happens:
1.	My computer beeps as (presumably) the login screen appears.
2.	The drum sound indicating that its time to login comes out of my other sound device, an EMU 0202 USB device, and not the SB-Live USB device (which was selected as the default).
3.	I log in.
4.	I now hear the login sound coming out of my SB-Live device (as it should).
5.	Orca begins to speak out of the SB-Live device (as it should).
Thus, the question is, why is the login bongo sound coming out of the EMU device if I have the SB-Live device selected as the default?  Is there any way to fix this?

Also, on a side note, can I get Orca to say “Login” or “Enter Login” when the login prompt first appears?  Thus, I’m looking for Orca to start at the system level before I actually log in.

Thanks.

--Pete

---

### Post by PreviousN on 2009-06-12
> why is the login bongo sound coming out of the EMU device

Haha. I'm sorry. I just couldn't handle that sentence. No wonder people don't understand technology with weird sentences like that. 

Anyways, I'm going to watch this thread since I'm interested. I'll take a swing at it if no one else does. I've never messed around with usb sound, but I have had to compile alsa from source before (which shouldn' be relevant now that we're using pulseaudio in ubuntu). In a side note, pulseaudio has some AWESOME configuration GUIs that ubuntu didn't install by default which may give you the ability to tweak your settings in an easier way. I'll paste the link here, give me a minute.

This may help you out: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Here's a link to the pulseaudio thing I was mentioning earlier in this post...
[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)
As you can see, there are a number of utilities that ubuntu has left out. 
```

    * PulseAudio Volume Control
    * PulseAudio Volume Meter
    * PulseAudio Manager
    * PulseAudio Device Chooser
    * PulseAudio Preferences 

```
I think ubuntu left out the manager, device chooser, and preferences. Good luck fixing your problem!

---

