---
title: "Bluetooth headset and ALSA vs. PulseAudio"
date: 2010-12-29
forum: Multimedia Software
---

### Post by Graeme.N on 2010-12-29
I running a fresh install of Xubuntu 10.10 on an Acer Aspire 3054WXMi laptop with a 3rd-party bluetooth USB dongle plugged into the side of it. - The bluetooth side of things appears to be working OK and I can pair my Samsung SBH-500 bluetooth headset and tell it to connect the "Headset service" or "Audio sink" seemingly OK, except ... I hear nothing thru' the headset, only thru' the laptop speakers.

I have read various postings about getting it working with ALSA or with PulseAudio - PulseAudio sounds easier, but the ALSA stuff is supposed to be installed already (including bluez-alsa), but doesn't seem to be working properly.

Where shall I look next?
Should I use ALSA or PulseAudio?

TTFN.,
Graeme

---

### Post by Graeme.N on 2010-12-30
Interesting info, Daniel, but it doesn't really help me, esp. as the benefits of PulseAudio you mention I probably won't be needing on this laptop.

So, should I be persuing resolving this bluetooth audio issue using ALSA or PulseAudio?  Or does it not matter?

---

### Post by perspectoff on 2010-12-30
I could only get my HDMI to work with Pulse Audio. YMMV.

I also use PulseAudio for streaming to my Airport Express (to which I have connected a remote sound system), which I can't do with ALSA alone.

Also, PulseAudio allows multiple inputs and outputs from/to different sources, and allows real-time variable mixing. 

It is quite powerful, but for the average situation absolutely unnecessary.

Stick with ALSA alone until you find a need for PulseAudio.

---

### Post by Graeme.N on 2011-01-11
So it has been suggested I stick with ALSA ... any ideas as to why it isn't working?

---

### Post by guberone on 2011-03-13
[http://ubuntuforums.org/showthread.php?t=1363714](http://ubuntuforums.org/showthread.php?t=1363714)

It been a while since your post but I used above to get logitech wireless heasdset H760 working yesterday in xubuntu 10.10.  I could not get headset to work with alsa alone, it showed in alsa but I could not figure out how to make it work.  Pulseaudio worked for me in terminal.

```
sudo apt-get install pulseaudio
```

```
sudo apt-get pavucontrol
```

Then go Multimedia>PulseaAudio Volume Control

Mess around with the settings in there.

I'm a newer to xubuntu & removed and reinstalled a couple times out of frustration. But then realized I was not putting my internal audio back to the correct setting in pulse after using headset. Initially was panicked thinking pulseaudio messed up my sound. I was wrong about that, but if you want to remove after installing the following worked for me.

```
sudo apt-get autoremove pulseaudio
```

```
sudo apt-get autoremove pavucontrol
```


Would like to know if I can make pulseaudio default sound control, or otherwise make buttons on headset work to adjust volume and such.  Buttons work on ubuntu 10.04 and wifes mint 10.10, but not on my xubuntu 10.10.  Headset audio works perfect on x but not headset control buttons.  Suggestions anybody?

---

### Post by dmizer on 2011-04-08
> **guberone said:**
> [http://ubuntuforums.org/showthread.php?t=1363714](http://ubuntuforums.org/showthread.php?t=1363714)

It been a while since your post but I used above to get logitech wireless heasdset H760 working yesterday in xubuntu 10.10.  I could not get headset to work with alsa alone, it showed in alsa but I could not figure out how to make it work.  Pulseaudio worked for me in terminal.

```
sudo apt-get install pulseaudio
```

```
sudo apt-get pavucontrol
```

Then go Multimedia>PulseaAudio Volume Control

Mess around with the settings in there.

I'm a newer to xubuntu & removed and reinstalled a couple times out of frustration. But then realized I was not putting my internal audio back to the correct setting in pulse after using headset. Initially was panicked thinking pulseaudio messed up my sound. I was wrong about that, but if you want to remove after installing the following worked for me.

```
sudo apt-get autoremove pulseaudio
```

```
sudo apt-get autoremove pavucontrol
```


Would like to know if I can make pulseaudio default sound control, or otherwise make buttons on headset work to adjust volume and such.  Buttons work on ubuntu 10.04 and wifes mint 10.10, but not on my xubuntu 10.10.  Headset audio works perfect on x but not headset control buttons.  Suggestions anybody?

Thanks for this. After completely giving up on bluetooth sound in Xubuntu, your post saved the day.

---

