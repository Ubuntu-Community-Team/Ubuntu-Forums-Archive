---
title: "Disabling graphics card's HDMI?"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Xipe_Totec on 2009-09-24
Ever since I switched my motherboards, I can't get any sound on my Jaunty. A more Linux savvy friend managed to narrow down the problem.

It seems my graphic card and my onboard sound card both use the same module - snd-hda-intel. Problem is, Ubuntu treats the graphics' HDMI as the default audio device, and almost doesn't even acknowledge the existence of the onboard sound card. I can see it via *lspci*, though. Lsmod says it's **also** using snd-hda-intel module as well.

Now, I'm naively thinking that, if I could disable the HDMI port/device, the system would default to the onboard card. Problem is, we don't know how to do it, _without disabling the hda-intel module_. All advice I found about it calls for a module to be blacklisted. That would, obviously, also disable the onboard sound card.

Here's some of the data:
*lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: Biostar Microtech Int'l Corp Device 821e
    Flags: fast devsel, IRQ 16
    Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
    Subsystem: PC Partner Limited Device aa30
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe9ec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Motherboard is Biostar G41D-M7
Graphics card is Sapphire ATI Radeon HD4850

If the whole disabling idea is too naive to work, could you suggest something else?

---

### Post by Xipe_Totec on 2009-09-24
After a LONG night trying various things, I can report the problem's sorted. In a very silly and basic way.

Removed **all** modules related to alsa using the tip from [here](http://www.alsa-project.org/~valentyn/Alsa-sound-mini-HOWTO-7.html) (bottom of the page). Afterwards I proceeded to [alsa page](http://www.alsa-project.org/main/index.php/Download) to download the latest source release, and I compiled it following the guidelines [here](http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html) (actually, the straightforward ./config -> make -> make install). Afterwards I only needed to increase the volume with alsamixer, and that's that.


Now lsmod | grep snd gives:
snd_hda_codec_atihdmi    11520  1 
snd_hda_codec_realtek   208260  1 
snd_hda_intel          35840  6 
snd_hda_codec          87168  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm                83844  3 snd_hda_intel,snd_hda_codec
snd_timer              29192  2 snd_pcm
snd                    67364  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm


alsa-info.sh, collected from [here](http://osdir.com/ml/fedora-list/2009-06/msg02519.html) gives:
> !!Loaded ALSA modules
!!-------------------
snd_hda_intel
snd_hda_intel

!!Soundcards recognised by ALSA
!!-----------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe8fc000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe9ec000 irq 17

!!PCI Soundcards installed in the system
!!--------------------------------------
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio

Meaning, module for graphics card and motherboard sound cards are separated.

It seems the topic is now redundant, but maybe it would help someone later on.


(Also, other links I found useful:
[http://wonkabar.org/2009/08/25/common-alsa-issues/](http://wonkabar.org/2009/08/25/common-alsa-issues/)
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/) )

---

