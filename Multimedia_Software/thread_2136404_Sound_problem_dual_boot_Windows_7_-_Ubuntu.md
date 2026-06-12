---
title: "Sound problem dual boot Windows 7 - Ubuntu"
date: 2013-04-17
forum: Multimedia Software
---

### Post by 8YDtTGwJRd on 2013-04-17
Hi, i installed Ubuntu in dual boot with Windows 7 (manual partition, no wubi) and i have this problem. When i use Ubuntu the audio works but it's in low quality ( I have an IDT audio card that needs HQ drivers to work properly), when i use Windows the audio it's in high quality because i installed the drivers. However when i reboot from Ubuntu to Windows the audio is still in low quality, it is as if Windows uses Ubuntu's drivers. Does anyone know how to solve the problem? Thanks

---

### Post by dabl on 2013-04-17
Your "IDT" audio card, model whatever, either is or is not well-supported by the ALSA drivers.  That can be your research project -- I would start by reviewing:

[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

and as shown, run this:

```
cd ~/
  wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Probably the ALSA driver that is being used in Ubuntu is leaving the audio chip in a state different from what the Windows driver is expecting. Windows can't "use" the Linux driver, but the chip can be set differently by different drivers, and left in different states at shutdown.  I would guess that if you actually power down the computer after a Ubuntu session, and leave it shut off for 5 minutes, and then power it on and boot Windows, the Windows driver will bring it up in a "normal for Windows" mode.

---

### Post by 8YDtTGwJRd on 2013-04-17
Thanks for your reply, you are right, if i boot directly from windows after i shut down the PC it works perfectly, i'll do what you suggest, is there anything else i should do?
Here is the output: [http://www.alsa-project.org/db/?f=b0c976314d8336daa3fb82ec840b9d4d637f983d](http://www.alsa-project.org/db/?f=b0c976314d8336daa3fb82ec840b9d4d637f983d)

---

### Post by dabl on 2013-04-17
Your sound system appears to be in good shape unless I'm missing something.  What makes you say it has "low quality"?  Do you mean "low volume"?

---

### Post by 8YDtTGwJRd on 2013-04-17
This is the control panel of IDT drivers for Windows. [http://s22.postimg.org/pc5qfyold/Cattura.png](http://s22.postimg.org/pc5qfyold/Cattura.png)I get the same audio quality of Ubuntu if i deselect "Beats Audio" I guess it enables an advanced audio configuration.

---

### Post by dabl on 2013-04-17
I don't know a lot about your particular laptop, although it looks like a very nice one, for 2008 vintage, and HP does normally turn out excellent products.  The Intel HDA chips are all pretty solid, and well-supported by the ALSA driver.  I would not be concerned about the comparison of eye-candy between the Windows GUI to their audio driver, versus Ubuntu's reliance on ALSA.  Audio quality is, after all, based on what you _hear_, not what you see on the screen.  You probably have some or all of these -- if not, go ahead and install them:

alsa-base
alsa-utils
alsamixergui
pavucontrol
pulseaudio
gstreamer0.10-pulseaudio
audacity

Now find a .wav or .ogg file of your favorite music, and play it with whatever player you like, including audacity if you want to see the waveform.   alsamixer in a terminal window, or alsamixergui will let you set the system volume level and default audio device.  pavucontrol will also let you choose inputs and outputs -- it is a layer above ALSA.  Play around and search in this forum for tips and other people's experiences.  I think your Ubuntu sound system is fine, and just needs the user to study up on Linux sound packages.  :)

---

### Post by 8YDtTGwJRd on 2013-04-17
You are probably right, it is possible that i just need to get used to the sound i hear, assuming this, is there anything i should do to fix the audio in Win7 or should i simply turn off the pc and then boot it directly ? (This is an objective problem because i sometimes hear statics even when the PC is not emitting any audio.) Thanks for all your support.

---

### Post by dabl on 2013-04-17
It looks like you need to shut the laptop down from Ubuntu and turn it off for a few minutes, before you boot Windows.  (Or, just use Ubuntu and don't bother with Windows ;-) )

---

### Post by 8YDtTGwJRd on 2013-04-18
Perfect, thanks again!

---

