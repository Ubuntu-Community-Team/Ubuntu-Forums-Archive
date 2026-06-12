---
title: "terrible sound from gigabyte motherboard"
date: 2011-06-02
forum: Multimedia Software
---

### Post by bobdobbs on 2011-06-02
Hi Guys.

I'm finishing setting up my new computer.
I'm installing ubuntu 10.04.
The motherboard is a gigabyte GA-H61M-D2-B3

When I plug the computer into my stereo, I get a horrible scratchy buzzing.

How can I get rid of it?

Thanks.

More info on hardware: 
> lspci -v | less gives a lot of output, including this:

> 
0:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fbff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


---

### Post by webofunni on 2011-06-02
Try adjusting the sound properties in the sound mixer available.

---

### Post by bobdobbs on 2011-06-02
> **webofunni said:**
> Try adjusting the sound properties in the sound mixer available.

Hi.

I've been playing with the dialogues under 'System'->'Preferences'->'Sound'.
I haven't managed to produce any satisfactory results.

If I play a youtube video, I can hear the video sound, but the crackling and hissing is very loud and overwhelms the sound from youtube.

---

### Post by webofunni on 2011-06-02
Are you sure that it is not the problem of your external speaker system or connectors. Do you have any other OS installed in system, are they able to produce sound in a betterway ?

---

### Post by bobdobbs on 2011-06-02
Yes.

I've got another computer plugged in to the same amp. Other computer is a laptop running ubuntu 11.04.

I've changed the cables around to test the amp input plugs and the cables.

It's definately the sound coming from the computer that is the issue.

> **webofunni said:**
> Are you sure that it is not the problem of your external speaker system or connectors. Do you have any other OS installed in system, are they able to produce sound in a betterway ?

---

### Post by lidex on 2011-06-03
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

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

