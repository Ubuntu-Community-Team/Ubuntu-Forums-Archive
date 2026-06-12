---
title: "[SOLVED] selecting a sound card and getting it to stick"
date: 2008-08-13
forum: Multimedia Software
---

### Post by devinWhalen on 2008-08-13
Hey,

I am having problems getting ubuntu to use the right sound card.  

I ran this:
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I want it to use card 1 and I think this will make the setting stick:
sudo alsactl store 1

Here is what I am running:
2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux


I want all sound to go to card 1.

Thanks for any help.

---

### Post by markbuntu on 2008-08-13
There are a few ways to do this, progressively more involved. 
Method 1.
In the volume control on the panel, right click on the little speaker and choose file/change device and choose the Ensoniq card, probably choice 1. Then go to System/Preferences/Sessions and choose save current session.
Method 2
Use asoundconf.gtk. This little app is very good if you have more than one sound card. You can get it with Synaptic and it lives in System/Preferences as Default Sound Card. Open it and choose Ensoniq.
Method 3
Use the Pulse Audio Volume Control, pavucontrol, also in Synaptic. It is found in Applications/Sound and Video. Open it and go to Output Devices. Right click on the output device that is your Ensoniq card. If you do this you can also set Default Sound Card to pulseaudio and control every application's volume and output device in the PA Volume Control. Like if you want one thing on the VIA headphones and another on the Ensoniq speakers.

For more about setting up your sound, go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by devinWhalen on 2008-08-14
Thanks for your help.  I will try it when I get home from work.

---

### Post by devinWhalen on 2008-08-17
So I tried method 1 and that didn't change anything, then I tried method 2 and I could choose the default sound card but there was no option to save it, just a quit button??

Anyway, I tried method three and then I also changed /etc/modprobe.d/alsa-base and added this to the bottom of the file:
options snd_ens1371 index=0
options snd_via82xx index=1
options snd_mpu401 index=2
 which sets my AudioPCI [Ensoniq AudioPCI] sound card as the first device, which is what I want.  So I rebooted and the sound that is made when the login screen loads was loud and clear.  Then when I logged in the initial sound that is made when you log in runs but once everything loads up and I try playing music or testing system sounds, it all goes back to the onboard sound, which I what I don't want.  If I run pavucontrol it still says that the card I set as default before is the default card but no sound is coming out.  Is there some sort of user setting I need to change?

Thanks for any help, this is really frustrating, I just want to play music on my computer.  The onboard sound is no where near loud enough.

Thanks.

---

### Post by markbuntu on 2008-08-18
Well, that is progress of some sort but your apps are still using the wrong card because that's what they used last time.

In pavucontrol, which is the Pulse Audio Volume Control, you can change the playing application's ouput  stream by right clicking on it and choosing move stream and choosing your ensoniq card. To get all the alsa/oss apps to play through the same pulseaudio control, change your default sound card to pulseaudio with asoundconf-gtk.

You can make these changes stick by using System/Preferences/Session/Save Current Session thingy. 

I change the streams around all the time because I have my headphones hooked up to my on board card and my speakers to my pci sound card. I have also set up a virtual device to direct the streams to both cards. You can read about how to do that and a bunch of other stuff here:

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

---

### Post by cooke77 on 2008-08-18
You still have your 'on-board Sound' Enabled?
What for?
If you want to use an 'add-in Sound card'.....on-board HAS to be Disabled.

---

### Post by markbuntu on 2008-08-18
> **cooke77 said:**
> You still have your 'on-board Sound' Enabled?
What for?
If you want to use an 'add-in Sound card'.....on-board HAS to be Disabled.

No it doesn't. 

I have both working on my machine and I use them both all the time.

---

### Post by devinWhalen on 2008-08-19
Thanks for everyones help, I finally got it solved!  So I noticed that 
pavucontrol fixed the default sound card for all the users on my box (just 2 others) but not the one I always use.  So I figured it obviously must be some sort of preference for my user.  I found a file called ~/.asoundconf.asoundrc (or something like that) and it had the wrong default sound card set up.  Don't know how that happened, but I must have done something wrong.  Anyway, I ran 
asoundconf list

To get all my cards and then ran

asoundconf set-default-card CARD

Where card was the name of the card I got from asoundconf list.

Anyway, I hope this can help someone else.  That was it.

Thanks for all the help.  This use to happen to me every time I would download a bunch of updates, so know I know how to fix it.

Thanks.

---

