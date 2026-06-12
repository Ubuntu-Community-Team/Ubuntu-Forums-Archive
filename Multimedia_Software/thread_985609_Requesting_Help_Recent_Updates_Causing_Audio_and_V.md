---
title: "Requesting Help: Recent Updates Causing Audio and Video Issues"
date: 2008-11-17
forum: Multimedia Software
---

### Post by Excelchan on 2008-11-17
Hello,

I just registered to the forum, because I have not had a need to post until now (I love Ubuntu :D).

Before I start to describe my problem, here are my specifications:
Laptop: System 76 Pangolin Performance
Processor: Intel Core 2 Duo P8400 2.26 GHz 1066 M
RAM:  4 GB - DDR2 800 MHz - 2 DIMMs
Graphics: An nVidia card
OS: Ubuntu Hardy Heron (8.04) 64-Bit
(Let me know if you need more specs, system is fully up-to-date besides the 8.10 release)

Fairly new to Ubuntu, (been using it for 6 months or so) I am having some serious issues with a recent update(s). I normally check (look through what they consist of) the items that are needing to be updated when I start the update manager. But, last night I had about one week of updates to install and without checking if there were any unsupported/beta updates, decided to click 'Install' and proceeded to shut down my computer for the next days work. 

After turning my computer on the next morning to check my emails, I noticed that I did not hear the normal 'Logon' sound that I would when Ubuntu would boot up. I did not think anything of it, until I tried to play music, movies, anime, etc and nothing would produce sound. I have spent the past couple of hours trying to find a solution to my issue, with no luck. Since I did not check the packages to be updated like I normally would have, I don't know what broke this, or how to fix it. YouTube videos will play fine, there is still no sound when they are running, though.

I have ran a few commands that I am not sure will help in hopefully getting my sound and/or video playback working again.

chris@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The analog (first entry) will usually say 1/1 when I first start ubuntu.

I have checked alsamixer; made sure nothing was muted that was important, as well as the master sound control. Nothing is muted, and I am stumped again. Reading that a recent update could have made pulseaudio hi-jack the ALSA 'drivers', I tried running pulseaudio from the command line. Here is the output:

chris@ubuntu:~$ pulseaudio
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0


Going to System -> Preferences -> Sound and running tests with any of the drivers, nothing will play back, via the speakers or headphones.

Please let me know if there is any more information I can provide to help get this issue resolved. I need sound to listen to customer voice mails, and I am having to use my Windows laptop currently >.>;

Oh, and if the answer is to update to 8.10, will this kill my VM Partition? I use Windows to run apps that don't work well with WINE.

Thanks,

-Excel

Edit: I restarted my system..seems that it will play videos now and have edited the post accordingly. As well, I am going to try to re-install the System76 Drivers and post what happens after this.

---

### Post by jerrylamos on 2008-11-17
My opinion, do NOT update to 8.10 without trying CD Live first.  Looking over the posts, many upgrades have resulted in a hung computer.  I use dual boot, experiment with one while using the other for applications.

Jerry

---

### Post by Excelchan on 2008-11-18
I tried re-installing the System76 drivers with no luck in getting audio to work again.

Any ideas, suggestions, anything?

Thanks

---

