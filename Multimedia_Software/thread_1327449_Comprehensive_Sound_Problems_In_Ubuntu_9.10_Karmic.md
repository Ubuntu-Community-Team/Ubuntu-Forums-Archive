---
title: "Comprehensive Sound Problems In Ubuntu 9.10 Karmic Koala"
date: 2009-11-15
forum: Multimedia Software
---

### Post by Bunnybugs on 2009-11-15
Well, lots of people have problems with sound in the new release... there are many theories about how to repair these problems... But, the only solution that worked is also the simplest, I'll explain:

Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!

Close all your applications, and reboot your system...

Sound should work fine from now on!

---

### Post by Blond on 2009-11-20
Does not work for me :(
I work with Kubuntu 9.10 but in my list of Hardware Drivers is no modem, only the NVIDIA driver 185

Help

---

### Post by Bunnybugs on 2009-11-20
> **Blond said:**
> Does not work for me :(
I work with Kubuntu 9.10 but in my list of Hardware Drivers is no modem, only the NVIDIA driver 185

Help

Well, Kubuntu s something else then Ubuntu... Never really used KDe-desktop environment... So, I don't know... have you tried the sticky thread: Comprehensive sound problems?

---

### Post by Raff1 on 2009-11-20
I have the problem that my login sound plays double and unregularily, even if my system sound is muted(!). After on my sound is muted all right.

> **Bunnybugs said:**
> 
Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!


I could not find the 'Software Modem'-driver option, or any options at all in that screen. All it says is "No proprietary drivers in use on this computer". I don't seem to have any options at all there. :-/

---

### Post by tkoco on 2009-11-20
After considerable troubleshooting, I am of the opinion that the pulseaudio server is broken again. The listed observations are for Karmic and were not present in Jaunty.

Observations:
#1) Install 3 sound devices (audio cards). Boot up. In a terminal window, do an "lsmod" command and note that the correct drivers have been installed. Then check the available devices in the hardware tab of the pulseaudio server management program. You will find that one of the devices is MISSING! All devices were available in Jaunty!

#2) Select a device as the output sound device. Play an audio file. It sounds ok. Install a splitter cable so that the output goes to the speakers and an input of a different card. Try playing the same audio file out of the same card. The audio will be choppy or even stop after a few seconds. This situation never happened with pulseaudio in Jaunty.
Remove the pulseaudio server with Synaptic Package Manager to force the use of ALSA. The problem goes away!

A variation of this situation occurs on the laptops. Typically the input of the sound device affects the mixer. Playing sounds are choppy. Removing pulseaudio and falling back to ALSA fixes the sound.

Additional observation: When pulseaudio was installed, Battle for Wesnoth would lock-up when you attempted to exit the game (plus little or no audio). After removing pulseaudio, all is working fine now. Just an FYI.

---

### Post by polytropos on 2009-11-20
I also am having a sound problem with Karmic.  I have sound after booting, and all is fine until the computer hibernates.  After reactivating from hibernation there is no sound - if I want sound I have to reboot.

Any thoughts?

---

### Post by alexfish on 2009-11-20
you can check your lap tops with this


from the terminal

aplay -l 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem] <--------This one
   Subdevices: 0/1
  Subdevice #0: subdevice #0


 if looks something like this 
 try to disable the software modem in the bios 

      also search site with the info it  gives

 there is a link here for laptops with hardware problems

[http://ubuntuforums.org/showthread.php?t=361237](http://ubuntuforums.org/showthread.php?t=361237)

---

### Post by Bunnybugs on 2009-11-20
> **Raff1 said:**
> I have the problem that my login sound plays double and unregularily, even if my system sound is muted(!). After on my sound is muted all right.



I could not find the 'Software Modem'-driver option, or any options at all in that screen. All it says is "No proprietary drivers in use on this computer". I don't seem to have any options at all there. :-/


okay, pulseaudio works fine here... as long as I keep the Software Modem driver out of business... but reusing alsa is a good solution, I hope it works for everyone!

---

### Post by Rrasyrogenees on 2009-11-20
i did not have the modem on mine either but i did have my creative x-fi listed before but now it is not and i cannot seem to add the driver but it does show my card on aplay -l... go figure... i have no sound now although i did have it before on karmic koala yet today it is all gone.


i guess i will need to learn how to program in linux so i can figure these things out myself...

---

### Post by Bunnybugs on 2009-11-21
Well, this could help... but I really doubt it: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by xx58 on 2009-11-23
:rolleyes:BunnyBugs is absolutly right, keep Software Modem Drive out of Business and Sound system will work like charm. Thank you BunnyBugs.

---

### Post by Bunnybugs on 2009-11-23
> **xx58 said:**
> :rolleyes:BunnyBugs is absolutly right, keep Software Modem Drive out of Business and Sound system will work like charm. Thank you BunnyBugs.

The software modem is one of the problems... there seems to be something else, but in the case of this driver, it's triggered by the driver. Keep it out of use, and it all works fine!

---

### Post by Uncle Spellbinder on 2009-11-23
> **Bunnybugs said:**
> Well, lots of people have problems with sound in the new release... there are many theories about how to repair these problems... But, the only solution that worked is also the simplest, I'll explain:

Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!

Close all your applications, and reboot your system...

Sound should work fine from now on!

No such entry:

---

### Post by Bunnybugs on 2009-11-23
Yeah, a lot of people don't even have this driver... but, if you have this driver listed, keep away from it. It's a trigger for the pulseaudio bug!

---

### Post by Bunnybugs on 2009-11-23
> **Bunnybugs said:**
> Yeah, a lot of people don't even have this driver... but, if you have this driver listed, keep away from it. It's a trigger for the pulseaudio bug! Here's the screen

---

### Post by freakrz on 2009-11-23
i have a HP HDX 16t, i was using Jaunty for quite some time now and have upgraded it to karmic..after the upgrade sound stopped working.I removed the pulse audio and reinstalled it.then I could here the start up ding sound.but after that there is no sound for any of the apps.

my sound card shows up in the list.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
	Subsystem: Hewlett-Packard Company Device 361b 
	Flags: bus master, fast devsel, latency 0, IRQ 22 
	Memory at dd000000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 
	Kernel driver in use: HDA Intel 
	Kernel modules: snd-hda-intel 

some reason I could'nt get the sound for the applications.any suggestions on how to deal with it.

---

### Post by Bunnybugs on 2009-11-23
> **freakrz said:**
> i have a HP HDX 16t, i was using Jaunty for quite some time now and have upgraded it to karmic..after the upgrade sound stopped working.I removed the pulse audio and reinstalled it.then I could here the start up ding sound.but after that there is no sound for any of the apps.

my sound card shows up in the list.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
    Subsystem: Hewlett-Packard Company Device 361b 
    Flags: bus master, fast devsel, latency 0, IRQ 22 
    Memory at dd000000 (64-bit, non-prefetchable) [size=16K] 
    Capabilities: <access denied> 
    Kernel driver in use: HDA Intel 
    Kernel modules: snd-hda-intel 

some reason I could'nt get the sound for the applications.any suggestions on how to deal with it.

Remove Pulseaudio complete from synaptic, and install ALSA again... heard from some people that it worked for them... But, if you have a software modem + driver, just deactivate the driver... that solves the problem to!

---

### Post by freakrz on 2009-11-23
Thanq Very Much...:D That Worked Perfect....!

---

### Post by powe309 on 2009-12-07
> **Bunnybugs said:**
> Well, lots of people have problems with sound in the new release... there are many theories about how to repair these problems... But, the only solution that worked is also the simplest, I'll explain:

Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!

Close all your applications, and reboot your system...

Sound should work fine from now on!

Thanks.  This seems to have worked for me so far.  I never had any problems with sound on my laptop before upgrading to 9.10 (I have an HP DV6700).  After the upgrade, sound would not work if I had it on mute prior to the last reboot.  Putting it on mute appeared to prevent the audio driver from being loaded on the next reboot.  While annoying, I didn't consider it too big a deal.  Unfortunately, after the last update sound quit working altogether.  After doing as suggested above, everything seems to be okay for now.  I guess I'll just have to wait and see if it breaks again.

---

### Post by Roger Allott on 2009-12-07
I'm going to give this solution a go, but before I do, would anyone like to tell me what useful purpose the software modem is meant to perform?

In other words, what will I be giving up in order to get sound?

---

### Post by Bearly Able on 2009-12-11
I don't have the "software modem" driver, but removing pulseaudio has solved all my sound problems.  Thanks, guys.

---

### Post by markbuntu on 2009-12-11
A software modem is used to generate modem sounds for a dial up connection. This can cause problems with other sound drivers if it is loaded before them and becomes the default driver. This has nothing to do with pulseaudio but with the alsa drivers which are still being used.

Regarding pulseaudio, if you have used another distro like Fedora or Mandriva you would realize that the problem is not pulseaudio so much as its continuing poor implementation in Ubuntu. This has perplexed the pulse devs since it has given pulseaudio such a bad reputation.

There is a reason why everything alsa except the low level drivers is being deprecated. It has a lot to do with moving the alsa drivers into the kernel and maintaining kernel security. Old protocols like dmix and esound do not accomplish this and allow applications direct access to the kernel which is a no no.

Now maybe that move was a little premature as the only thing that was available to replace alsa at the time was a very buggy and by no means ready for release pulseaudio that was hurriedly and poorly adopted in time for the release of Hardy Heron 8.04.  Pulseaudio has improved dramaticaly since then but not much in Ubuntu due to some very poor decision making by the ubuntu maintainers and some incomplete work by the gnome people in moving the gnome volume control to pulseaudio. Just recently they have started working in earnest with the pulse devs to get pulseaudio in ubuntu and in gnome straightened out finally and completely for Lucid Lynx. We may even see pulseaudio 1.0.

---

### Post by l-x-l on 2009-12-11
I think I figured out part of the problem with sound. On 12/9/09, there was an update to the flashplugin-installer. It went from version 10.0.32.18ubuntu1 to 10.0.42.34ubuntu0.9.10.1. Since then, whenever I use my browser to watch a video stream (youtube), flash seems to high-jack my audio & doesn't let anything else come out of my speakers until I close the browser. After that sound works for other applications as normal.

There seems to be an issue with Pulse & the flash-plugin. Anyone have any ideas?

---

### Post by PatrickPredella on 2010-02-23
My problem is a bit different... Two days ago the sound worked. Now it looks like ubuntu doesn't find anymore the sound hardware.

---

### Post by coty24 on 2010-03-02
> **Bunnybugs said:**
> Well, lots of people have problems with sound in the new release... there are many theories about how to repair these problems... But, the only solution that worked is also the simplest, I'll explain:

Just go to your Hardware Drivers menu (System>Administration>Hardware Drivers)...

Select the 'Software Modem'-driver... and press Remove!

Close all your applications, and reboot your system...

Sound should work fine from now on!

That worked for me ! Thank you

I have a HP Touchsmart tx2-1025 dx
Running x64 Karmic
Woot!

---

