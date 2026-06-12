---
title: "[SOLVED] USB Headphone Problems"
date: 2008-09-05
forum: Multimedia Software
---

### Post by fejy on 2008-09-05
I just bought a new USB headset and got it to work by both changing all options in sound preferences to "USB Audio" and by changing the default ALSA audio device to "Headset" using asoundconf. After successfully switching back to my PC speakers and rebooting, I am no longer able to use the USB headphones. When I select "USB Audio" in the sound preferences and click "Test", I get this error:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback

and no sounds will play. Speakers still work fine.


```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ asoundconf list
Names of available sound cards:
SI7012
Headset
```

---

### Post by fejy on 2008-09-05
I setup the PulseAudio Server for the headset and it is functional (sound, microphone working) but it has taken over the volume controls of the headset, making the built-in controller unusable. Although the device is now working, I'd still like to get it back to full functionality.

EDIT: PulseAudio is also apparently fairly useless for the applications I need the headset for.

---

### Post by fballem on 2008-09-05
I have a working setup, so let me share it with you - no guarantees that it will work for you, but might get you started on the right track.

[LIST=1]
[*]Install asoundconf-gtk. This can be done from System > Administration > Synaptic Package Manager (search for 'asoundconf' and install) or from terminal (sudo apt-get install asoundconf-gtk). When done, you should have a menu item System > Preferences > Default Sound Card.
[*]Open System > Preferences > Sound. This will open the gnome-sound-properties application.
[*]The attached screenshot shows how I have set my system. Save and close when done.
[*]To change from Speakers to Headphone (or vice-versa), 
[LIST=2]
[*]open the Default Sound Card option (System > Preferences > Default Sound Card). This will open a small window (see the Full Screen screenshot - my window is in the upper-right corner).
[*]when you click on the up/down arrow in the window (see Default Sound Card screenshot) you will get a list of the sound devices that are enabled for ALSA. Click on one, then select the Quit button. This will change the sound device and close the window.
[/LIST]
[*]The selection will be valid the next time you start an ALSA enabled application. This currently works for Exaile and VLC. You may need to configure the Preferences in the applications to use ALSA.
[/LIST]

Hope this helps,

---

### Post by fejy on 2008-09-05
Thanks, although that setup did not initially solve the problem,
asoundconf-gtk provides a nice gui for the commands I was running with just asoundconf. I fixed the problem by deleting /etc/asound.conf. I am now able to easily switch between speakers and USB headphones.

---

### Post by fballem on 2008-09-05
> **fejy said:**
> Thanks, although that setup did not initially solve the problem,
asoundconf-gtk provides a nice gui for the commands I was running with just asoundconf. I fixed the problem by deleting /etc/asound.conf. I am now able to easily switch between speakers and USB headphones.

Do you have to exit the application in order to switch, and do you use asoundconf-gtk to make the switch?

Just curious in case there's a better solution than the one that I found.

---

### Post by fejy on 2008-09-08
> **fballem said:**
> Do you have to exit the application in order to switch, and do you use asoundconf-gtk to make the switch?

Just curious in case there's a better solution than the one that I found.

Yes, I now use the asoundconf-gtk to switch with the Autodetect options, although selecting the individual sound cards "USB Audio" and my on-board sound card in Sound Preferences works now also. Yes, I do have to close the applications and reopen them for the change to happen.

---

