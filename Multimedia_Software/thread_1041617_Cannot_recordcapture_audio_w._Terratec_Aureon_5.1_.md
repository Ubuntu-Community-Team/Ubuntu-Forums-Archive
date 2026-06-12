---
title: "Cannot record/capture audio w. Terratec Aureon 5.1 USB MK.2 and Alsa."
date: 2009-01-16
forum: Multimedia Software
---

### Post by Willard on 2009-01-16
Greetings!

Could someone help me out? I have a Terratec Aureon 5.1 USB MK.2 , and am trying to get it to replace my built-in sound card while at home (I would like to be able to switch between using the external USB soundcard, and the internal on-board Intel one for when I am not at home). Very specifically, I would like to be able to hear mplayer and record with xvidcap on my Terratec.

I am part-way there, but I have run into a snag. Info on my sound devices:

```
willard@njordur:~
> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

willard@njordur:~
> arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have tried using the .asoundrc file from [http://alsa.opensrc.org/index.php/Terratec_Aureon_5.1_USB_MK.2](http://alsa.opensrc.org/index.php/Terratec_Aureon_5.1_USB_MK.2) , with slight modifications ( instead of 'pcm "hw:0,0"', I have used 

```
pcm { type hw
      card "Audio" }

```

The full file:
```
willard@njordur:~
> cat .asoundrc
pcm.dmix51 {
  type dmix
  ipc_key 1024
  ipc_key_add_uid false
  ipc_perm 0666
  slave {
     pcm {
         type hw
         card "Audio"
         }
     channels 6
     period_time 0
     period_size 1024
     buffer_size 8192
     rate 44100
  }
}

ctl.dmix51 {
  type hw
  card "Audio"
}

pcm.stereo {
  type plug
  slave.pcm "dmix51"
  ttable.0.0 1
  ttable.1.1 1
}

pcm.!default {
  type route
  slave.pcm "dmix51"
  slave.channels 6
  ttable.0.0 1
  ttable.1.1 1
  ttable.0.2 1
  ttable.1.3 1
  ttable.0.4 0.5 
  ttable.1.4 0.5 
  ttable.0.5 0.5 
  ttable.1.5 0.5 
}

pcm.duplicate {
  type plug
  slave.pcm "dmix51"
  slave.channels 6
  route_policy duplicate
}

```

So far, I can hear sound through the Terratec when playing a video with 'mplayer -ao alsa file.mpeg' (I need the option, or else I get no sound in mplayer). Also, Alsa's speaker-test works.

```
willard@njordur:~
> speaker-test

speaker-test 1.0.15

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left
Time per period = 2,808179
 0 - Front Left
Time per period = 2,987028
 0 - Front Left
...

```

If I un-mute my Mic in 'alsamixer -Ddmix51', I can hear my mic through the speakers. So far, so good.

But if I try to record sound with Alsa, I get this error.

```
willard@njordur:~
> arecord hat.wav
ALSA lib pcm_dmix.c:813:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
arecord: main:546: audio open error: Invalid argument

```

Also, setting everything to "Alsa" in 'gnome-sound-properties' works for everything except for "sound capture". There, on testing, and if I try running 'gnome-sound-recorder', I get the error

```
gconfaudiosrc ! audioconvert ! audioresample ! gnomeaudiosink profile=chat: Could not open audio device for recording.

```

If I try recording with xvidcap anyway, and play back the result, the sound is just white noise.

How to I record "capture streams"? Seems dmix cannot do that. Can I specify in .asoundrc that "something else" should be used for that? If so, how?

Also, is there a convenient way to toggle which device is my default sound playback/capture device? I wish to just specify "Use the Terratec soundcard", or "Use the built-in Intel soundcard", for when I am at, or away from, home.

Do I need to fiddle with pulseaudio any?

Information on my platform, an ASUS F8SA Notebook ([http://www.asus.com/products.aspx?l1=5&l2=26&l3=501&l4=0&model=1591&modelmenu=1](http://www.asus.com/products.aspx?l1=5&l2=26&l3=501&l4=0&model=1591&modelmenu=1)) :

```
willard@njordur:~
> uname -a 
Linux njordur 2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux 
 
willard@njordur:~
> cat /proc/cpuinfo  
processor : 0 
vendor_id : GenuineIntel 
cpu family : 6 
model : 15 
model name : Intel(R) Core(TM)2 Duo CPU T7300 @ 2.00GHz 
stepping : 10 
cpu MHz : 800.000 
cache size : 4096 KB 
physical id : 0 
siblings : 2 
core id : 0 
cpu cores : 2 
fpu : yes 
fpu_exception : yes 
cpuid level : 10 
wp : yes 
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida 
bogomips : 3995.11 
clflush size : 64 
cache_alignment : 64 
address sizes : 36 bits physical, 48 bits virtual 
power management: 
 
processor : 1 
vendor_id : GenuineIntel 
cpu family : 6 
model : 15 
model name : Intel(R) Core(TM)2 Duo CPU T7300 @ 2.00GHz 
stepping : 10 
cpu MHz : 800.000 
cache size : 4096 KB 
physical id : 0 
siblings : 2 
core id : 1 
cpu cores : 2 
fpu : yes 
fpu_exception : yes 
cpuid level : 10 
wp : yes 
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida 
bogomips : 3990.01 
clflush size : 64 
cache_alignment : 64 
address sizes : 36 bits physical, 48 bits virtual 
power management: 

``` 

Help much appreciated.

Best regards,
Willard.

---

### Post by markbuntu on 2009-01-16
Alsa is not so easy to use with multiple sound devices but with pulseaudio you can do all that very easily. If you need information about setting up the pulseaudio sound server you can go to the Sound Server Setup section here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Willard on 2009-01-16
Thank you. I'll look into that.

I got things more or less working on my end by configuring .asoundrc in my home directory. The error I got was because dmix, which is for playback software mixing, cannot be used for capture software mixing. You need dsnoop for that.

Most of my .asoundrc came from
[list][*][Terratec Aureon 5.1 USB MKII @ opensrc.org](http://alsa.opensrc.org/index.php/Terratec_Aureon_5.1_USB_MK.2)[/list]
I modified it slightly to suit my purposes, by use of information from
[list]
[*][Asoundrc](http://alsa.opensrc.org/index.php/Asoundrc)
[*][Dsnoop](http://alsa.opensrc.org/index.php/Dsnoop)
[*][AlsaSharing](http://alsa.opensrc.org/AlsaSharing), explaining how to mix both capture ad playback.
[*][Dmix](http://alsa.opensrc.org/DmixPlugin)[/list]

Here is my .asoundrc.
```
willard@njordur:~
> cat .asoundrc
pcm.dmix51 {
  type dmix
  ipc_key 1024
  ipc_key_add_uid false
  ipc_perm 0666
  slave {
     pcm {
         type hw
         card "Audio"
         }
     channels 6
     period_time 0
     period_size 1024
     buffer_size 8192
     rate 44100
  }
}

ctl.dmix51 {
  type hw
  card "Audio"
}

pcm.dsnoop2 {
    type dsnoop
    ipc_key 34523
    slave {
      pcm {
          type hw
          card "Audio"
          }
    channels 2
    period_size 1024
    buffer_size 4096
    rate 48000
    periods 0 
    period_time 0
    }
}

pcm.!default {
    type asym
    playback.pcm "dmix51def"
    capture.pcm "dsnoop2"
}

pcm.dmix51def {
  type route
  slave.pcm "dmix51"
  slave.channels 6
  ttable.0.0 1
  ttable.1.1 1
  ttable.0.2 1
  ttable.1.3 1
  ttable.0.4 0.5 
  ttable.1.4 0.5 
  ttable.0.5 0.5 
  ttable.1.5 0.5 
}

pcm.stereo {
  type plug
  slave.pcm "dmix51"
  ttable.0.0 1
  ttable.1.1 1
}

pcm.duplicate {
  type plug
  slave.pcm "dmix51"
  slave.channels 6
  route_policy duplicate
}

```

Cheers,
Willard.

---

