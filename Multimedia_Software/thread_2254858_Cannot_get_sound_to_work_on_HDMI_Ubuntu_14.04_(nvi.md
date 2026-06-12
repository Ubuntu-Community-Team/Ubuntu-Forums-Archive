---
title: "Cannot get sound to work on HDMI Ubuntu 14.04 (nvidia HDMI not detected)"
date: 2014-11-30
forum: Multimedia Software
---

### Post by shbharga on 2014-11-30
Hello,

I have been trying to get HDMI sound to work for the past few days, but nothing has worked so far. To get it out of the way, I am connecting a Samsung 27" monitor with HDMI and it works in windows, so it shouldn't be a hardware/cable issue. I also cannot find a way in my BIOS to force using nvidia card.

_**My system:**_
OS: Ubuntu 14.04 64-bit, uname -r gives me "3.13.0-40-generic"
I have Nvidia 860M with Intel graphics with optimus (Lenovo Y50)

The underlying problem seems to be that nvidia HDMI is not detected, as I get the following output from _**aplay -l**_:
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: ID 2807 Digital [ID 2807 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC283 Digital [ALC283 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

_**glxsphere**_ gives me:
```
glxsphere: command not found
```

_**optirun glxsphere**_ gives me:
```
[ 1309.747302] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver


[ 1309.747389] [ERROR]Aborting because fallback start is disabled.

```

Though let me clarify that I would be happy if I just get the damned sound from Intel card. I dont need/want to do any graphics heavy stuff in linux so I don't care about nvidia card being detected unless its needed for sound.

_**What I have tried:**_
[LIST=1]
[*]Installing and reinstalling pulseaudio
[*]Installing and reinstalling nvidia drivers separately
[*]Installing and reinstalling bumblebee (after purging nvidia-current and bumblebee*). I guess I dont have to install nvidia drivers myself in this case? Bumblebee takes care of it? Though should I be doing
```
sudo apt-get purge nvidia*
``` 
before installing bumblebee? It shows me some 190 MB of stuff to be removed. I'm scared of removing that much, but I ead you have to remove all nvidia drivers that you installed yourself before installing bumblebee
[*]Changing the grub file **/etc/default/grub**
```
GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="acpi=force" or GRUB_CMDLINE_LINUX="nvidia.audio=1"
```
[*]Adding the following lines to the end of the file **/etc/modprobe.d/blacklist.conf**
```
blacklist nouveau
blacklist nvidiafb

```
[/LIST]

I have rebooted after doing any step. None of these have worked correctly. At some point I had HDMI audio but it was very distorted (at any sound level) everything was high pitched and squeaky. I did the above steps again, and now I don't have sound as before. At some point I also ran into the error of "ubuntu is running in low graphics mode", but solved it with installing bumblebee. Basically I haven't made any progress in all of my attempts. It is quite annoying as I have to switch to Windows if I want to take a break from work and just watch a video, and I end up taking longer breaks than I should/ would :P

Thank you in advance!

---

### Post by marc-defossez-c on 2014-12-06
Hi,

Have exactly the same issue on a DELL M6800 with Intel Haswell adn Nvidia Quadro K3100M graphics cards.
Nvidia works fine when PC is plugged into the docking station with two monitors connected (each on one HDMI port).
      Sound goes via the headphoen output.
Nvidia works fine whan a home entertainment center is plugged into the on board HDMI port.
       Sound should go over HDMI to the system, but it does not.

Reason:
      Nvidia HDMI is not recognized at all.
      I've done all teh same tests as shbharga and get the same results. INTEL HDMI detected, NVIDIA not.
      In System Settings --> Sound there is not HDMI item that can be selected.
      Pulse Audio Volume Control --> Configuration shows HDMI entries but these are aways market as unplugged.

Tried lots of provided answers in other treads but none worked. (change grub line, add /etc/asound.conf file and etcetera).

I found one thing on teh Nvidia web site. The file /proc/asound/cards shiuld contain entries for all video cards but one my PC it only contains entries for Intel.
Maybe an hint for somebody knwoing lots more about this that I.

Kind regards,

---

### Post by SeijiSensei on 2014-12-06
We have a Lenovo laptop with an NVIDIA card.  It has a small switch on the front that you can flip to force the machine to use that adapter.  If yours is similarly equipped, you might give that a try.

---

