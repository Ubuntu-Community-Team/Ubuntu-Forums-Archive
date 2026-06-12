---
title: "Sound Problems!"
date: 2009-06-02
forum: Multimedia Software
---

### Post by Goddard on 2009-06-02
I am new to Ubuntu and I'm having difficulties setting up my sound to work properly.

Here is what I get after typing 

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech Wireless Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I can play music, but that is about the only sound I can get working through the sound control panel.....

---

### Post by Goddard on 2009-06-02
I added some more information.

---

### Post by kostkon on 2009-06-02
What problems do you have exactly?

If you want to easily control to which audio device (I can see you also have a USB headset) the sound of an application goes then you need to install the PulseAudio Device Chooser utility. Also, from there you will be able to set the default audio device for your system.

For more info, check [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by Goddard on 2009-06-03
Thanks for the info got it working.

---

### Post by Goddard on 2009-06-03
I take that back.  The reason I got it working was...I did a reinstall, but once I install Skype and Flash plugin for firefox and disable accessibility and removed orca I restarted and now I have no login sound just static!!!

---

### Post by Goddard on 2009-06-03
This is really werid.  I literally did nothing to mess with my sound settings!! Somebody help me out here!! this is so annoying!!!

HOW DO I RESTORE UBUNTU SOUND SETUP TO DEFAULT AND KEEP IT THAT WAY!!!

---

### Post by redenex on 2009-06-03
> **Goddard said:**
> This is really werid.  I literally did nothing to mess with my sound settings!! Somebody help me out here!! this is so annoying!!!

HOW DO I RESTORE UBUNTU SOUND SETUP TO DEFAULT AND KEEP IT THAT WAY!!!

I can understand your frustration ever since I installed 9.04 Beta 64 bit a few months ago. But as luck would have it, I did a re-install of Jaunty last week, and surprisingly I got my sound working (it still has problems though). Once I play a song, it gets cut off after sometime, but once I go to the terminal, press backspace (to invoke the system beep), the sound comes back!

Good luck with your issue, someone might be able to help and there are atleast 10-12 informative threads in the site.

---

### Post by Goddard on 2009-06-03
I already reinstalled once is the thing and had perfect sound then all of a sudden it just stops working after a reboot.  It is so annoying.

---

### Post by redenex on 2009-06-03
I can understand that frustration, I did installation almost 9 times, but luckily things are okay for me except for the problem above mentioned. I am sure I can sort that out soon as well.

---

### Post by Goddard on 2009-06-03
Where are the sound settings saved? Is it one configuration file or multiples?  Sure would be nice to just save a copy of it and then put it back if thats even possible????

Save the settings when you first install and then if some how it buggers up again just put the save config files back in.

---

### Post by Goddard on 2009-06-03
It has something to do with the auto detection settings I know that because when it first installs it auto detects perfectly maybe a update screwed the auto detection settings?  Any ideas or help here would be good Ubuntu peoples

---

### Post by Goddard on 2009-06-03
I found the settings file and set it correctly now I have perfect sound every where.....damn that was easy.  I also disabled Ubuntu sounds.

---

