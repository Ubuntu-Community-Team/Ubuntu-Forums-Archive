---
title: "Sigmatel STAC9200: no sound. Help needed."
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by Master_Z on 2007-06-26
My sound chip is a Sigmatel STAC9200 (High Definition Audio Codec). Feisty Fawn detects the card and shows it on the alsamixer, as well as the sound preferences. I've tried switching to alsa, but that didnt work. The funny thing is that I can increase and decrease the volume, and the icon in the corner isnt muted, but I Have no sound. In Rhythmbox, it will actually show the song streaming, but I cannot hear it. Is there any way to fix this? I am DESPERATE for help.

---

### Post by 5-HT on 2007-06-26
I have the same chip running on an Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller. Are you using the same controller (you can check by doing a 'lspci')?

What happens when you try to use ALSA? You may not have the module (snd_hda_intel) loaded
```
sudo modprobe snd_hda_intel
```

I'd stick with making sure that all the appropriate channels are unmuted and at a proper level via alsamixer as your sound applet could be monitoring a different channel right now.
Here are all the sound related modules I have running, if you're running the same hardware as I am, try loading these (sudo modprobe module_name) if not already loaded, and switching to ALSA from the sound preferences option in the menu.

```
snd_seq_oss
snd_seq
snd_seq_device
snd_pcm_oss
snd_hda_intel
snd_hda_codec
snd_mixer_oss
snd_pcm
snd_timer 
```

cheers

---

### Post by Master_Z on 2007-06-27
All of them worked but the snd_hda+codec. It said it did not exist. And it didnt help, as I still have no sound. :(

Anyone else have a solution to my problem ?

---

### Post by dabl on 2007-06-27
I have the same chip and Intel HDA system on my motherboard -- it works great, for recording and playing.  I'll attempt some pointers:

1. Right-click the little speaker icon in the upper right corner of your Ubuntu desktop.  Choose "Preferences".  Set the little window at the top to "HDA Intel (ALSA Mixer)".

2. Right-click the little speaker icon in the upper right corner of your desktop again. Choose "Open Volume Control".  Choose "Edit" and "Preferences".  Make sure there is a checkmark in _every _box in that menu.

3. While you have the "Volume Control" open, on the "Playback" tab, make sure that the left two sliders, "PCM" and "Front" are NOT muted.  It's OK if the others are muted -- at least it is OK on my system. On the "Switches" tab, it needs to to show the IEC958 box checked.

4. If your keyboard has a volume control on it, press "+" or up to make sure you have some volume that way.

5. Speakers need to be turned on (not trying to be insulting, just gotta check off all the possibilities).

6. I've noticed that Firefox can "hijack" the sound output channel, so shut down Firefox, then try to play a music file.

I hope one of these helps!  :D


P.S. For software packages, I have the following installed:

alsa-base
alsamixergui
alsa-oss
alsaplayer-alsa
alsaplayer-common
alsaplayer-gtk
alsaplayer-oss
alsa-utils

---

### Post by Master_Z on 2007-06-27
> **dabl said:**
> I have the same chip and Intel HDA system on my motherboard -- it works great, for recording and playing.  I'll attempt some pointers:

1. Right-click the little speaker icon in the upper right corner of your Ubuntu desktop.  Choose "Preferences".  Set the little window at the top to "HDA Intel (ALSA Mixer)".

2. Right-click the little speaker icon in the upper right corner of your desktop again. Choose "Open Volume Control".  Choose "Edit" and "Preferences".  Make sure there is a checkmark in _every _box in that menu.

3. While you have the "Volume Control" open, on the "Playback" tab, make sure that the left two sliders, "PCM" and "Front" are NOT muted.  It's OK if the others are muted -- at least it is OK on my system. On the "Switches" tab, it needs to to show the IEC958 box checked.

4. If your keyboard has a volume control on it, press "+" or up to make sure you have some volume that way.

5. Speakers need to be turned on (not trying to be insulting, just gotta check off all the possibilities).

6. I've noticed that Firefox can "hijack" the sound output channel, so shut down Firefox, then try to play a music file.

I hope one of these helps!  :D


P.S. For software packages, I have the following installed:

alsa-base
alsamixergui
alsa-oss
alsaplayer-alsa
alsaplayer-common
alsaplayer-gtk
alsaplayer-oss
alsa-utils

Okay, let me tell you what I did for your instructions.

1) It was already at ALSA Mixer (mine isnt HDA_Intel though, its HDA ATI SB)
2) Some of them were not checked, so I DID check them all, making them all visible.
3) IEC958 is indeed checked and they arent muted.
4) I hit fn and vol up (its a laptop), and the volume is shown to increase, I set it to max.
5) They are built in and already on.
6) I did all of this and shut down firefox and tried opening rhythmbox. Sadly, there was still no sound.

Do you have any other tips?

---

### Post by Master_Z on 2007-06-28
Bump. Please someone, having no sound is like torture.

---

### Post by dabl on 2007-06-28
That is truly a bummer.  Did you have any sound with the live CD?  I guess I would try flipping the whole deal over to OSS, if ALSA won't work.  :(

Depending on your level of desperation and willingness to do experiments, there is a Linux distro called e-live that has about the most amazing sound, by default, that I've run across.  I'm not sure it has a lot else to offer, but you might want to try making a live CD and see how it handles your hardware.  Here's the Live CD site, for the "unstable" development version, which downloads way faster than the "stable" version: [http://www.elivecd.org/gb/Download/Development/](http://www.elivecd.org/gb/Download/Development/)

I hope I don't get disbarred from Ubuntu for this ....

---

### Post by Master_Z on 2007-06-29
Does this elive have more sound support than Feisty? And btw, I tried switching to OSS, but that didnt work either.

---

### Post by dabl on 2007-06-29
Well, on my system, I can tell you that e-live sound just works -- zero configuration issues.  It's a spartan little Debian Linux desktop, you don't see much unless you click your mouse on the desktop to make menus appear.  I have it on an old IDE drive that I only use to collect backups from Ubuntu and Kubunto.  But it automatically configured the sound system, runs XMMS radio, plays music files, and seems to be rather rugged, in terms of recognizing the hardware and configuring itself accordingly.  If nothing else, it might configure itself on your hardware, and give you some insight into how the mixer needs to be set up to play your STAC chip.

:)

---

### Post by osarusan on 2007-07-07
I have a SigmaTel STAC9228, so I thought this thread might help me. I did manage to get one step further I think...

I added: options snd-hda-intel model=SigmaTel STAC9228 to the end of my alsa-base file. I still can't play music or sounbs, BUT the system beep works! So I think I'm on the right track. I don't know what to do next though. :-( Any ideas?

---

### Post by Haz13r on 2007-07-07
I have the EXACT same model.  I have a Dell computer but what i did was just restart my computer and it worked.  Haha.

---

### Post by bakketti on 2007-07-19
Just got a new Dell Inspiron 1420 (originally installed with Vista). I am also having the exact same problems as explained on this post (however with a STAC 9228 ) .  Tried everything that was suggested... and no luck. 

Isnt this the same chipset that the Ubuntu Inspiron 1420 are running? I'd assume it would work out of the box.

---

### Post by osarusan on 2007-11-01
> **Haz13r said:**
> I have the EXACT same model.  I have a Dell computer but what i did was just restart my computer and it worked.  Haha.

Just for the record, can you post the last part of your /etc/modprobe.d/alsa-base file? I want to see how it compares to mine... I still can't get my sound to work. :(

---

### Post by mameman on 2008-04-18
i am having the same problem. I have the same card and i downloaded some ALSA related programs but nothing happened then i decided to restart my computer and when it ame back the little volume icon on the top right had a little x i thought it was muted but when i clicked on it it get this

No volume control GStreamer plugins and/or devices found.

it hasnt had that before i restarted and now when i goto sound options there is no device on the last option HDA alsa nor the Sigmatel STAC9200 appears but now the system beep works but nothing else.

PLEASE HELP NO SOUND ON GUTSY GETS BORING. IT MAKES WANT TO GO BACK TO M$ WINDOWZ

---

