---
title: "Ubuntu 7.04, SB Audigy, and no sound."
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by bartek212 on 2007-06-28
I know the Sound Blaster Audigy is popular so I decided to write here after reading something about Sound Troubleshooting.

I hope someone experienced can take a look and say what's wrong:

> 
aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: CK804 [NVidia CK804], urz&#261;dzenie 0: Intel ICH [NVidia CK804]
  Urz&#261;dzenia podrz&#281;dne: 0/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: CK804 [NVidia CK804], urz&#261;dzenie 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: Audigy [Audigy 1 [SB0090]], urz&#261;dzenie 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Urz&#261;dzenia podrz&#281;dne: 32/32
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
  Urz&#261;dzenie podrz&#281;dne #1: subdevice #1
  Urz&#261;dzenie podrz&#281;dne #2: subdevice #2
  Urz&#261;dzenie podrz&#281;dne #3: subdevice #3
  Urz&#261;dzenie podrz&#281;dne #4: subdevice #4
  Urz&#261;dzenie podrz&#281;dne #5: subdevice #5
  Urz&#261;dzenie podrz&#281;dne #6: subdevice #6
  Urz&#261;dzenie podrz&#281;dne #7: subdevice #7
  Urz&#261;dzenie podrz&#281;dne #8: subdevice #8
  Urz&#261;dzenie podrz&#281;dne #9: subdevice #9
  Urz&#261;dzenie podrz&#281;dne #10: subdevice #10
  Urz&#261;dzenie podrz&#281;dne #11: subdevice #11
  Urz&#261;dzenie podrz&#281;dne #12: subdevice #12
  Urz&#261;dzenie podrz&#281;dne #13: subdevice #13
  Urz&#261;dzenie podrz&#281;dne #14: subdevice #14
  Urz&#261;dzenie podrz&#281;dne #15: subdevice #15
  Urz&#261;dzenie podrz&#281;dne #16: subdevice #16
  Urz&#261;dzenie podrz&#281;dne #17: subdevice #17
  Urz&#261;dzenie podrz&#281;dne #18: subdevice #18
  Urz&#261;dzenie podrz&#281;dne #19: subdevice #19
  Urz&#261;dzenie podrz&#281;dne #20: subdevice #20
  Urz&#261;dzenie podrz&#281;dne #21: subdevice #21
  Urz&#261;dzenie podrz&#281;dne #22: subdevice #22
  Urz&#261;dzenie podrz&#281;dne #23: subdevice #23
  Urz&#261;dzenie podrz&#281;dne #24: subdevice #24
  Urz&#261;dzenie podrz&#281;dne #25: subdevice #25
  Urz&#261;dzenie podrz&#281;dne #26: subdevice #26
  Urz&#261;dzenie podrz&#281;dne #27: subdevice #27
  Urz&#261;dzenie podrz&#281;dne #28: subdevice #28
  Urz&#261;dzenie podrz&#281;dne #29: subdevice #29
  Urz&#261;dzenie podrz&#281;dne #30: subdevice #30
  Urz&#261;dzenie podrz&#281;dne #31: subdevice #31
karta 1: Audigy [Audigy 1 [SB0090]], urz&#261;dzenie 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Urz&#261;dzenia podrz&#281;dne: 8/8
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
  Urz&#261;dzenie podrz&#281;dne #1: subdevice #1
  Urz&#261;dzenie podrz&#281;dne #2: subdevice #2
  Urz&#261;dzenie podrz&#281;dne #3: subdevice #3
  Urz&#261;dzenie podrz&#281;dne #4: subdevice #4
  Urz&#261;dzenie podrz&#281;dne #5: subdevice #5
  Urz&#261;dzenie podrz&#281;dne #6: subdevice #6
  Urz&#261;dzenie podrz&#281;dne #7: subdevice #7
karta 1: Audigy [Audigy 1 [SB0090]], urz&#261;dzenie 3: emu10k1 [Multichannel Playback]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0


It's in Polish because I have no idea how to change the language in console.
I also have integrated sound card on my DFI NF4 Infinity, and it's famous AC'97 :P I've tried to plug my headphones to its output also, but seems like there's also no signal at all!

Thank You in advance!

---

### Post by bartek212 on 2007-06-28
Anyone? :(

---

### Post by MorphingJar on 2007-06-29
go to your terminal and type in 

```
alsamixer
```

then scroll all the way over to the right until you get to "Audigy Analog/Digital Output Jack."  Turn if off by pressing "M".    The little box should say "MM"

---

### Post by bartek212 on 2007-06-30
Well, I've had a sound after I do that what You said (thanks) but only until the reboot. After reboot when I type "alsamixer" in terminal I can't see any Audigy record (only Realtek bars). What happened and why?

---

### Post by MorphingJar on 2007-07-01
the changes should take.  But if not.  Try using the command as "sudo"

```
 sudo alsamixer
```

This will use the code as "root".  Which is basically the "Administrator" of linux.

---

### Post by inuyokai on 2007-07-01
I swear sound is random in ubuntu...

I'm running into the same problem with an Audigy card. Its really odd too because I've had sound before, then installed Wine 0.9.39 and installed Counter-Strike and played a bit with sound. Then, Wine updated to 9.40 and the sound in CS started to lag behind if it even worked at all. I then tried using JackAudio which didnt help and now I have no sound at all...

alsamixer does not work all of the time nor does sudo alsamixer so that doesnt really help anyone. I've previously used asoundconf to set-default-card Audigy and asoundconf set-pulseaudio and it was partially responsible for giving me sound the first time, now it does nothing but give me the following error ```
ALSA lib control.c:875:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

Any help with how to run k/ubuntu with sound would be awesome. I've ran other Linux OS's and PC-BSD and they all had sound, this is the only distribution I've had a problem with.

bartek212

I'm not really experience but here is how I got sound to work the first time.

In Terminal

```
asoundconf list
```

This will list sound cards available - if Audigy (which is what yours will probably come up as, if not then whatever your card is).

Now type

```
asoundconf set-default-card yourcardname
```

My card shows up as Audigy so where it says "yourcardname" type Audigy

Next

```
asoundconf set-pulseaudio
```

Close terminal and go to Kmix (or whatever Gnome's mixer is if you use Gnome) and open it. Make sure your card is selected and then click the switches tab. Turn off the Audigy Analog/Digital Output.

If that doesnt bring sound on right away then ctl-alt-backspace and restart.

If you still dont have sound then you're in the same boat as me.

---

### Post by bartek212 on 2007-07-01
inuyokai, great, how to recover my alsamixer now? :P After Your commands I'm getting Your error:

> ALSA lib control.c:875:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory
bartek@ubuntu:~$ asoundconf list


---

### Post by inuyokai on 2007-07-02
You know... Its odd because I just reconfigured all of my settings and I did all of the same commands except for asoundconf set-pulseaudio.

Try asoundconf unset-pulseaudio and then alsamixer.

You have to set your default card or once you get into alsamixer you wont be able to adjust that cards settings.

The way I got sound back was probably more drastic than the route you'll want to go but here is how it happened. I decided to see what Gnome was like so I reinstalled (I havent been running this distro long so I had no files), I hated Gnome so I reconfigured KDE. Before I installed Gnome I was messing with these commands and found that pulseaudio is causing the problem (mine at least). What I did after installing was removed every package in the multimedia area that had to do with sound (actually I think it was every package) and then I did the following commands.

```
asoundconf set-default-card Audigy
```

Again, Audigy is my card so use yours.

```
alsamixer
```

This finally got me into the mixer where I scrolled over and turned off Audigy Analog/Digital Output by pressing M. I turned all of the other volumes up and restarted X and the sound came on.

I suggest trying 

```
asoundconf unset-pulseaudio
```

and then trying the other commands. If that doesn't work then uninstall the packages in multimedia and try again.

Sorry man....

Like I said, I think sound is random...

---

