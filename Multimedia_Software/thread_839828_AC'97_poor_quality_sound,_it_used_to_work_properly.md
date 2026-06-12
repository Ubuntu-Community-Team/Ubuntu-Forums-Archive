---
title: "AC'97 poor quality sound, it used to work properly :S"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Copitox on 2008-06-24
Hi everyone!

I've used Ubuntu for almost 3 years, but just with this new 8.04 i have had this problem. The thing is i DO have sound, and it always word pretty well natively, i never install any sound drivers. The problem it's that one day i just turned on my PC, and strangely music sounds AWFUL, my music files sound like if they had very low bitrates, but in my Windows partition they are OK. The weird thing is that i didn't do a thing, just checked my mail, watched some youtube videos and that's it. This problem came out from nothing.

What could it be? Last time that happened (this is not the first time) i had to reinstall ubuntu, i don't want to do that again :(

thanks!

PS: sorry for my bad english, im from southamerica.

---

### Post by Copitox on 2008-06-25
Up!

---

### Post by Copitox on 2008-06-25
No help?

---

### Post by markbuntu on 2008-06-25
Ok, a few questions.

Is it just your music files or all sound that has turned bad?

What application are you using to liten to your music with?

What are the settings in Administration/Preferences/Sound?
and Administration/Preferences/Multimedia Systems Selector/Audio if you have that?

---

### Post by Copitox on 2008-06-25
> **markbuntu said:**
> Ok, a few questions.

Is it just your music files or all sound that has turned bad?

What application are you using to liten to your music with?

What are the settings in Administration/Preferences/Sound?
and Administration/Preferences/Multimedia Systems Selector/Audio if you have that?


Thanks for the answer! 

I'm not sure, but i think that just my audio files sound strange, i've been using Banshee, but i tried with a few more application and it's the same.

The settings on Preferences/Sound are all on Autodetect and in Dispositive it's SiS SI7012 (Alsa Mixer)

I don't have the second manu you say.

thanks!!

---

### Post by markbuntu on 2008-06-25
Try playing a music file in Rythmbox or some other music player.

I don't use banshee so I am not sure but there may be a setting for changing the bitrate of the audio and it may have gotten reset somehow.

The AC'97 works fine in Ubuntu so really it is just a matter of figuring out which setting got messed up somewhere. The only problem is there are a lot of somewheres.

---

### Post by Copitox on 2008-06-25
> **markbuntu said:**
> Try playing a music file in Rythmbox or some other music player.

I don't use banshee so I am not sure but there may be a setting for changing the bitrate of the audio and it may have gotten reset somehow.

The AC'97 works fine in Ubuntu so really it is just a matter of figuring out which setting got messed up somewhere. The only problem is there are a lot of somewheres.


It's sounds terrible with every music player i've tried :(.

The strange thing is that i dind't change any setting, the only audio thing i did was installing ubuntu-restricted-extras for the codecs and stuff.

thanks!

---

### Post by markbuntu on 2008-06-25
OK, try this, Go to Admin../Pref.../Sound and try changing the Sound Playback to Alsa or Pulseaudio Sound Server instead of Autodetect.

---

### Post by Copitox on 2008-06-25
> **markbuntu said:**
> OK, try this, Go to Admin../Pref.../Sound and try changing the Sound Playback to Alsa or Pulseaudio Sound Server instead of Autodetect.

Tried every option, still not working ok :(:(

---

### Post by markbuntu on 2008-06-26
Sorry for the late reply but sleep, work, etc...

We need to check that your sound card is being properly detected.

In a terminal type.

lspci

This will list all your pci hardware. You should see a line like

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

---

### Post by aeiah on 2008-06-26
before delving into changing sound architectures, drivers etc etc you should probably:
a: go to youtube, play a video, and turn the volume to 80% instead of 100%
b: open your volume control applet (mine is at sound & video > volume control) and make sure the sliders aren't set higher than 80%. my onboard soundcard distorts if i have one of the sliders on max.

simple but worth checking before messing with other stuff i guess

---

### Post by Copitox on 2008-06-27
copitox@desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
**[SIZE="4"]00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)[/SIZE]**
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

is there something wrong?

---

### Post by Copitox on 2008-06-27
WTF it works fine now :S :S!

This come up from nothing! ill test it later with more time!

---

