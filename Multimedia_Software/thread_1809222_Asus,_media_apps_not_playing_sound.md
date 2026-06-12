---
title: "Asus, media apps not playing sound"
date: 2011-07-21
forum: Multimedia Software
---

### Post by Oblivio on 2011-07-21
Yesterday I installed drum kit programs.
Then I noticed sound didn't  work &#8594; I unmuted "internal" in GNOME Asla Mixer and it was okay. Today I  unmuted internal in GNOME Alsa Mixer(also checked sound GUI preferences  and alsamixergui) and no change, the sound still won't work.

My  media players open but don't play - like they forgot how to perform an  mp3 after 0:00. Youtube plays normally but without sound.

If anyone has any sort of idea of what is going on or how to fix it please share.

More information below.

___::
I've had tons of trouble with my sound card (VIA VT1708S) - the  usual only-internal-speakers-work-when-heaphones-plugged-in problems.  But I could at least listen on the speakers. Now even that is gone and  the media players seem to be on strike!

They register  whatever commands I give (play, stop, volume, move window, ...), they  just don't do anything about it.

I have installed rosegarden and hydrogen which automatically installed  Qjack and Banshee I think. I had rhytmbox before and have just removed it.

Weird part is, when I went into Gnome Alsa yesterday and  unchecked mute on internal it started working fine - but today it did  not have an effect. I did hear a click in my headphones when I unchecked  it for the first time today but that's about it.

If I check my  audio settings everything looks in order, the output device is set to  analogue but testing the speakers does nothing except crashes the sound  preferences window.

GNOME ALSA Mixer says my card is "VIA VT1807S"
alsamixergui says my chip is "PulseAudio"

"lspci -v" yields:
> Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 1523
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fbcf4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by lidex on 2011-07-21
Did you boot into windows in the interim? If so, boot into windows then reboot from that into ubuntu without shutting down. 
Try a suspend/resume cycle. 
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Lastly, try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Oblivio on 2011-07-21
Sound started working again - completely randomly before I had a chance to test the settings. I will test them the next time my sound stops working and get back to you.

Note: A reboot into the paralel system occured so that could be the solution.

**EDIT:

Thanks, lidex, the reboot was enough. Though for the record whenever I restarted Jack (qjackctl) my sound system would go bananas until its next complicated reboot, after which I would have needed to re-set the settings in alsa.

Funnily enough, my Hydrogen dk works without jack running... and I can only hear it on my headphones while there's Bobby McFerrin playing on the computer's internal speakers. I hate the relationship between my computer and Linux but at times like this it just cracks me up.

---

