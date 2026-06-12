---
title: "How to disable HDMI output using analog same module?"
date: 2016-01-16
forum: Multimedia Software
---

### Post by cris6 on 2016-01-16
Hi

I am having problems with audio with Ubuntu (all versions) and Elementary OS

I have an Acer (E1) notebook which has Radeon HDMI output, but the problem is that both outputs (analog and HDMI) use the snd-intel-hda module, so I don't know how to disable or blacklist the hdmi part

The system tries to use the HDMI output by default, and I can't change it to the analog output

I am using fglrx-updates drivers

aplay - l gives this

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: CX20584 Analog [CX20584 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I could change asound.conf to this
> pcm.!default {
    type hw
    card 1
}

ctl.!default {
    type hw           
    card 1
}

But the problem is that after a few seconds of working audio the system disabled the output and forced the damn HDMI output again


Anyway to disable the HDMI sound ? Or anyway to blacklist only the HDMI module without losing all sound  ?


I had this problem with all flavors of Ubuntu (and I even tried Ubuntu 16 to test) and Elementary OS, and still could not find a proper way to disable the HDMI audio for real

Tks

---

### Post by Bucky Ball on 2016-01-17
Open Pulseaudio Volume Control (install if you don't have it). Go to the config tab. Choose your analogue device as the primary port rather than your HDMI device.

Have a tweak with PAVControl and see what you come up with. You shouldn't need to be tweaking code at this point.

---

### Post by cris6 on 2016-01-17
Hi

I am having problems with Pulseaudio, since it is conflicting with ALSA settings

I could change alsa conf file to only start the analog output by adding to the end "options snd-hda-intel enable=0,1" abd before changing that line, Pavu control (and audio settings at Elementary only showed HDMI output)

But the problem is that even with the OS only showing the analog output Pulseaudio "takes over" the settings and only outputs sound to the HDMI since there is no sound here
When I play anything Pavucontrol show that there is sound actvity being sent to the analog output, but no sound at all

I even tried to purge Pulseaudio from the OS to only use Alsamixer but the sound applet does not appear at the top of the Elementary OS taskbar

Do you know what I could to make it work, or even a way to block for real the HDMI ?

Tks

---

### Post by Bucky Ball on 2016-01-17
Are you wanting support with Elementary or Ubuntu? They are not one and the same.

---

### Post by SeijiSensei on 2016-01-17
On Ubuntu I would leave pulseaudio alone and install pavucontrol.  As Bucky said, that's really all you need.

---

### Post by cris6 on 2016-01-19
I did everything and still no audio, and not only on Elementary
Tried Ubuntu(14, 15 and 16), Xubuntu (16), Kubuntu (16, but it did not install, only used live), Ubuntu Studio (14 and 15), Mint (Cinammon and MATE 17.3 ) and still no sound
Sometimes sound works for a few minutes, but after that, HDMI becomes the only active output and nothing works more

So that applies to all distros, so it looks like a conflict regarding ALSA and outputs that use the same modulo (snd_hda_intel)

Anything I can possible use to fix it ?

I saw a site about modifying the kernel, by disabling HDMI outputs, but I could not pass the menu config util since the last time I modified and compiled a kernel was more than 15 years ago when I used a command line slackware distro....

Tks

---

### Post by Bucky Ball on 2016-01-19
For this support thread, please stick with Ubuntu, not Elementary. We do not give support for it in this section of the forums (and minimal support in 'Ubuntu/Debian based'). If you are wanting to persist with Elementary, best to seek help on their forum.

Switching between distros is confusing while we are attempting to help you on a support thread. If you want help here, install a Ubuntu, tell us which one it is, and we'll try to help you fix the problem on that install. Thanks.

---

### Post by cris6 on 2016-01-19
As I said the problems occurs on Ubuntu (and Ubuntu based distros, like Ubuntu Studio. Xubuntu and Kubuntu)
If any Ubuntu distro (Ubuntu pure or based distro) would fix the problem I would check their alsa conf files to see what was different or even use the distro where the sound problem was fixed, but that problem happens with Ubuntu 14, 15 and 16, since I have been testing them for a fw days with no luck at all

The problem appears to be the fact that since the sound module is the same for both HDMI and analog outputs, the system prioritizes the HDMI output, even with nothing plugged in the HDMI output, and the attempts I made to alter the order of the devices failed.

So again, since this is something that happens with Ubuntu (and other Ubuntu flavors) is there a real way to fix it  ?
In my other machine (netbook) there are 2 modules (one for HDMI, other for analog output) that problem does not happen, what makes it look that this is a problem regarding the way the OS handles the module, and of course, since there is 1 module for both outputs, I can't blacklist it, since it would disable audio for the entire system.

Tks

---

### Post by SeijiSensei on 2016-01-19
In Kubuntu, did you run System Settings > Multimedia > Audio and Video Settings > Audio Hardware Setup?  Did you see both playback interfaces and choose the analog option?

You should almost never need to touch ALSA on any modern Ubuntu system.

---

### Post by cris6 on 2016-01-19
Hi
I did check the audio settings, and they worked just for a few mins, and then, HDMI output becomes the "only" valid output
Is there a way to block only the HDMI output ?

Tks

---

### Post by SeijiSensei on 2016-01-19
That sounds like a bug in the Radeon driver to me.  Is there an older version of the driver than the fglrx-updates version you are using that you can try instead?  

I have a four-year-old HP laptop with a Radeon card, and I've never had the problem you describe.  If I switch from HDMI to analog and back again, it just remains fixed on the correct device.

---

### Post by cris6 on 2016-01-20
Hi

The problem happens with the open driver too

And I also have a netbook with radeon drivers that analog output works fine, since they use different modules

The main problem with this notebook is that it uses the same module to both outputs, and the OS is only using the HDMI part after just a few seconds of use

Tks

---

