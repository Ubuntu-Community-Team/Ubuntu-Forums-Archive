---
title: "rs880 audio device[Radeon HD 4200] doesn't work"
date: 2010-12-27
forum: Multimedia Software
---

### Post by JonasCoelho on 2010-12-27
Hi there,
I recently installed Ubuntu on my HP Pavilion dv4-2012br and am really enjoying it, except that it is conflicting with my sound card.
 The only way I can hear some sound is going into System> Preferences> Sound> Output and selecting "Internal analog stereo audio" which makes the sound hollow and not at all pleasant to listen to music. When I mark "RS880 audio device [Radeon HD 4200] Digital Stereo (HDMI)" the sound is not played.

 I followed step by step these instructions:
 [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
 yet the only way to run the audio through the "Internal analog stereo audio. "

 Is there any way to solve?
 Thank you in advance.

Just adding: I used the "Install with Synaptic Package Manager" way to do it. And i'm using a desktop version of Ubuntu.
Here are some screenshots:
[http://img23.imageshack.us/img23/1671/screenshotxux.png](http://img23.imageshack.us/img23/1671/screenshotxux.png) (Software Sources)
[http://img29.imageshack.us/img29/3810/screenshot1pub.png](http://img29.imageshack.us/img29/3810/screenshot1pub.png) (Synaptic Package Manager)
[http://img266.imageshack.us/img266/2061/screenshot3k.png](http://img266.imageshack.us/img266/2061/screenshot3k.png) (Sound preferences)

---

### Post by rainwater98 on 2010-12-29
Hi, it looks like we are having a similar problem.

I can hear audio through "Internal Audio" but not "RS880 Audio Device [Radeon HD 4200]." 

I am using Ubuntu 10.10. If I click on the Sound icon on the top right of the screen, go to sound preferences > hardware > test speakers. There are two "drivers:" Internal Audio and RS880 Audio Device. The only speakers that work are the Internal Audio.

Is it possible to get the RS880 Audio Device working?? 

Many thanks!!

---

### Post by lidex on 2010-12-29
You do know that hdmi does not play internally. You need to run an hdmi cable to a capable device.

---

### Post by JonasCoelho on 2010-12-29
> **lidex said:**
> You do know that hdmi does not play internally. You need to run an hdmi cable to a capable device.

I did not get it. Can't I use my notebook built-in speakers? Õo
They work greatly on Windows... o.o

---

### Post by lidex on 2010-12-29
> **JonasCoelho said:**
> I did not get it. Can't I use my notebook built-in speakers? Õo
They work greatly on Windows... o.o

Yes, you can, but with analog output, not hdmi.

---

### Post by JonasCoelho on 2010-12-30
Oooooooh, now it makes sense.
I tough that it should be activated because the bad quality of all the sounds played by Ubuntu, but It seems to be due to another reason...
Thanks anyway ^^

---

### Post by lidex on 2010-12-30
How is the audio quality bad? Can you describe?
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by JonasCoelho on 2010-12-31
The sound is the same when you take headphone on the max and hear them without introducing in your ear, while in Windows it has lots of "Sound effects" like a Home Theater.
I made as you said and a new option(Bass Speakers[It is not editable]) appeared at AlsaMixer but the sound is still "hollow".

[SIZE=4]
Happy New Year everyone![/SIZE]

---

### Post by lidex on 2010-12-31
It may need to be enabled. Probably gnome-alsamixer is best for that.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by JonasCoelho on 2011-01-03
I did that but everything was already enabled. Õo
 I was looking in the manual and I remembered that this model of laptop I'm using has a "Premium Sound ". I wondered if the sound driver for Ubuntu does not support "code" sound so that It can enjoy the full potential of the speakers. Is it possible?

---

### Post by JonasCoelho on 2011-01-11
Any idea?

---

