---
title: "Resolving sound settings issues for Dell Inspiron 640m"
date: 2013-02-19
forum: Multimedia Software
---

### Post by aburgesser on 2013-02-19
I am having some issues with the sound settings in Ubuntu 12.10 on my Dell Inspiron 640m laptop.

Sound works fine out of box, but if I select the item from the "Play sound through" list of the "Output" tab of the sound settings, my account's sound is broken until I remove the ~/.pulse directory.

The item in question is "Digital Output (S/PDIF): Built-in Audio". I repeat, selecting this item breaks sound.

I need this resolved so that I can't inadvertently break sound in the settings menu. Adding a valid element to the "Play sound through" list is preferred.  Also acceptable right now is to remove the item that breaks the sound (assuming there is not a case where I would want it).

I have made some dartboard changes (appending data to some configs, adding repos, and installing packages) before finding the fix I mentioned earlier. Lacking a convenient way to roll back package installations, I have let those be.

Thank You for any help in resolving this.

To provide supplemental information (ask if you need additional info):
```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 01d8
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
```

---

### Post by csillva on 2013-02-19
At a guess, I'd say you don't have a "Digital Output (S/PDIF): Built-in Audio" on your audio card, so selecting it causes a bug that renders your audio inoperative.

I'd recommend filing a bug upstream.

> I need this resolved so that I can't inadvertently break sound in the settings menu. 

Sorry to be flippant, but the old joke comes to mind:

Patient: Doctor is hurt's my arm when I do this <raises arm>. How do I make the pain stop?

Doctor: Don't do that anymore.

---

### Post by aburgesser on 2013-02-19
> **csillva said:**
> 
Sorry to be flippant, but the old joke comes to mind:

Patient: Doctor is hurt's my arm when I do this <raises arm>. How do I make the pain stop?

Doctor: Don't do that anymore.
 
Probably had that coming, but this was originally caused by an errant click. I then spent several hours trying to troubleshoot the sound. I'd rather make sure this can't happen again. Especially as it takes a restart to fix the issue.

---

### Post by Yellow Pasque on 2013-02-19
It shouldn't take a full system restart, just:
```
rm -r ~/.pulse*; pulseaudio -k
```

Oh, and  if you're going to post a bug, make sure you make a verbose log and click the digital output so devs can see exactly what happens: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by SeijiSensei on 2013-02-19
```
root@shiny:~# lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
        Subsystem: Dell Device 01d8
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel

```

I also have a 640m but get very different results from this command.  Yours returns "Capabilities: <access denied>" whereas mine returns a list of "Capabilities."  Maybe it's a permissions problem?

But, yes, there is no digital output that I'm aware of on a 640m, so even if the choice is offered, you should select the analog mode.

---

### Post by aburgesser on 2013-02-21
It was a permissions problem. Using sudo matches you results exactly. I would normally do this stuff as root, but I want to ensure that hardware will work completely before doing many usability tweaks.

Thanks for confirmation that the 640m can't do digital.

Is there some configuration file I can edit to remove digital output from the GUI settings menu?

As far as bug reports go, it seems the true bug here is a misidentification of hardware capabilities.

---

### Post by SeijiSensei on 2013-02-21
I don't think it's a "bug," because the digital hardware exists on the motherboard so Linux sees it.  The hardware just isn't connected to anything.

I use Kubuntu, where you can remove unwanted sound devices in System Settings.  I can't help with regular Ubuntu, but I'd be surprised if it's not possible there as well.

---

