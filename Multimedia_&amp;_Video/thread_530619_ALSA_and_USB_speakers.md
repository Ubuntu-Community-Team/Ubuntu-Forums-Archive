---
title: "ALSA and USB speakers"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by dbsears on 2007-08-20
I recently bought some USB speakers (Samsung Pleomax PSP-7000W, based on the C-Media CM102 chip) to install on my PC running Feisty Fawn. I've tested these speakers on an iMac and a Windows laptop without problems. The C-Media chip literature says that "no driver is necessary for audio playback on all major OS", which implies that the chip should be compatible with ALSA and the snd-usb-audio driver. Also, I've tested my PC's ALSA sound system with conventional speakers and it runs fine using the motherboard's on-board audio interface.

The USB audio device does appear on the USB bus:

  % lsusb -v
    ... C-Media Electronics, Inc.

  % cat /proc/bus/usb/devices
    ... S:  Manufacturer=C-Media INC.

  System>Preferences>Hardware Information
    ... UHCI Controller
    UHCI Host Controller
      ...
      Generic USB Hub
      ...
      C-Media USB Audio

But the USB audio device is not registered under ALSA: it doesn't appear in /proc/asound/cards and "asoundconf list" doesn't mention it. "modinfo snd-usb-audio" indicates that the USB audio driver is installed.

I did follow the instructions in [http://alsa-project.org/main/index.php/Matrix:Module-usb-audio](http://alsa-project.org/main/index.php/Matrix:Module-usb-audio)
I copied the contents for /etc/modutils/alsa and changed the slot and card numbers from 0 to 1 in the example. At this point, the alsa doc says to run update-modules, but that is obsolete and it's not clear how to do this with the new module-init-tools package. I tried rebooting, but no luck.

# ALSA portion
alias char-major-116 snd
alias snd-card-1 snd-usb-audio
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-1 snd-card-1

# card #2
alias sound-service-1-0 snd-mixer-oss
alias sound-service-1-1 snd-seq-oss
alias sound-service-1-3 snd-pcm-oss
alias sound-service-1-8 snd-seq-oss
alias sound-service-1-12 snd-pcm-oss

That's it. Thanks for any help.

--Dan

---

### Post by mohnkern on 2007-08-21
Try Typing:

asoundconf list

and see what comes up.

---

### Post by dbsears on 2007-08-21
Thanks for your help. I found (and should have known) that USB speakers don't like to be attached to USB hubs.

--Dan

---

### Post by gwenn59 on 2007-10-16
Hello,

I bought PSP800 speakers but I didn't found how to make them work. Can you explain a little bit more what you download and how you manage to solve the problem?

Didn't you compile the kernel or prefered the quick installation way?

Thanks a lot for your help.

---

### Post by SMcE on 2007-10-18
gwenn59

the easy way to get USB speakers to work with Ubuntu (I have found) is to use applications that allow you to switch soundcard. The following work for me:

xmms     
audacity
mp3blaster (mp3blaster --mixer-device='/dev/mixer1' --sound-device='/dev/dsp1'  works for me)

You need to check the options under the preferences menus for xmms and audacity - I can't remember the details right now.

---

### Post by ozmont on 2007-11-29
I dont know if anyone has run into this before but there is a trick to it (suprise, suprise)

Go to your synaptic and load xmms as a sound device, when you go into the preferences in there you will see and option to configure the alsa settings. In the device list will be your labtec speakers, select them as the device.

Now test the playback in xmms, if it iss OK go back and look at the preferences. Odds are it will read something like hw:1,0

this is a key to getting everything working. now go to your xine engine (preferably in master of the universe mode)set the audio driver from auto to alsa,  and set the output devices for audio mono and stereo to the hw:1.0 value.

You may need to repeat this for other multimedia apps, bui it does work, I am listening to my labtec USBs as I type.

good luck
:guitar:

---

### Post by jeffspen on 2008-02-04
hi
my problem is that my USB soundcard works fine in totem and rhythmbox but not for xine which I use in mythtv. I typed asoundconf list and it gives me my onboard Intel HDA and PCM2702 which is my Silverstone EB01.

How do I load xmms as an audio device as mentioned above?

---

