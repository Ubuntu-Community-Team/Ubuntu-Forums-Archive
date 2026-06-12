---
title: "Got ALC889A sound to work in Hardy"
date: 2008-08-02
forum: Multimedia Software
---

### Post by charlesbh on 2008-08-02
After a few weeks of fruitless effort, I managed to get sound working today. I thought I would pass on the experience.

Machine: Ubuntu Hardy, AMD64, Gigabyte GA-MA78GM-S2H equipped with a RealTek ALC889A codec. As far as I can tell, I am running a vanilla gnome ALSA setup.

Problem: couldn't get microphone input to work at all, making skype and ekiga use somewhat problematic. In addition, the front panel headphone jack didn't work.

Debugging: ALSA detected my codec as an ALC885. I found several posts that indicated that it would work better as an ALC883. I downloaded the ALSA drivers from realtek ([http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)). According to the code, the 889A is detected and set to be an ALC882. There is a note in the code that the ALC883 might be a better choice. I compiled and installed this code, but nothing changed. The codec was still thought to be an 885. I installed these drivers, and nothing changed. My codec was still an 885.

Further analysis showed that my 889A has a revision number of 0x100101, where the ALSA driver (alsa-kernel/pci/hda/patch_realtek.c) expects a rev of 0x100103. Apparently there is more than one 889A in the wild.

Steps to fix this problem:
1. Extracted the alsa drivers archive from the realtek tarball.
2. Modified patch_realtek to recognize the 889A with rev 0x100101. I made changes in two places (the lookup table and in patch_alc885), but I think that the lookup table change is enough.
3. Modified the install script supplied in the realtek archive to put the kernel driver modules in the right place (ubuntu/sound/alsa-driver instead of kernel/sound).
4. Modified the install script not to re-extract the alsa drivers tarball and not to delete the alsa drivers directory hierarchy when finished, avoiding the loss my precious changes.
5. Modified the install script to also include USB audio (I have a headset).
6. Ran install. I added the necessary development packages until everything compiled. (I don't remember which ones, sorry.)
7. Reboot.

Voila. head /proc/asound/card0/codec#0 now produces
Codec: Realtek ALC889A
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x1458a002
Revision Id: 0x100101

New situation: using 'patch_alc883', my front panel jacks and microphone input work. Sound recorder, skype, and Ekiga all work.

Note: From strings in the kernel alsa drivers, I think that the official ALSA source has (not working) ALC889A changes in it, but I haven't checked.

---

### Post by nunquamsecutus on 2008-09-06
First off, thank you for posting this.  Though my sound symptoms are not the same (see [http://ubuntuforums.org/showthread.php?t=889321]("http://ubuntuforums.org/showthread.php?t=889321") that post), the problem seems to be similar.  So here is what I did:

I installed libncurses-dev  (it was the only package I needed).

line 15996 in alsa-driver-1.0.17-5.07/sound/pci/hda/patch_realtek.c
	replaced:
		{ .id = 0x10ec0885, .rev = 0x100103, .name = "ALC889A",
	with:
		{ .id = 0x10ec0885, .rev = 0x100101, .name = "ALC889A",

line 9-14 in install
	commented out

line 97-100 in install
	commented out

line 7615-7616 in alsa-driver-1.0.17-5.07/configure
	replaced:
		    if test -d /lib/modules/$kaversion/kernel; then
      			modsubdir="kernel/sound"
	with:
			if test -d /lib/modules/$kaversion/ubuntu; then
				modsubdir="ubuntu/sound/alsa-driver"

Now head /proc/asound/card0/codec#0 gives:
> Codec: Realtek ALC889A
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x1458e601
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM


This is good, but aplay -l gives me:
> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


So instead of having the scraching terrible audio I had before, now I have no audio.  I checked in pulseaudio manager and it says that it thinks the device is the ALC 885 Analog, and I think this is the problem.  Anyone know how to make pulseaudio recognize the changes?

---

### Post by sandena on 2009-04-26
Hi I just built my pc with a gigabyte GA-MA78GM-US2H MB. Well I ran the live cd (ubuntu 9.04) and I had problems with audio (Realtek 889A). I barely hear the audio, the mic was dead. 
I didn't intall the Op. system because I never used Ubuntu before, I'm novice and I just wanted a Operating System running in my new machine. Unfortunately I don't know nothing about command line or change files in ubuntu. I tried folow the steps cited, but it looks confused to me. 
Well, Is there a easy way to install this things or put the audio working?
sorry I was a windows user, but now I'm looking forward to be free, UBUNTU. I don't wanna be leashed anymore, but unfortunately has been hard to me understand all this things. 
Please help me

Thanks

---

