---
title: "Confused with alsamixer setup."
date: 2017-03-22
forum: Multimedia Software
---

### Post by Bucky Ball on 2017-03-22
[QUOTE=]In order to record from a device, the device's "capture" switch must be set. To do so, run alsamixer, select your microphone and press space.[/QUOTE]

[From here]("http://alsa.opensrc.org/Record_from_mic"). I see it, but not sure which mic! I've tried them all.

I have an old STA Audio ADC/DAC device with Xubuntu-core 16.04 LTS on a machine that can handle it (i7, 16Gb RAM, built for purpose, etc. ...). This audio device is also known as the Hoontech DSP24 and the card is the ICE1712. It consists of two PCI cards. An eight channel audio interface attaches to one of the cards (multi) and the other card is a 'consumer' card with the regular ins/outs you would find on a standard, but very dated, audio card; a mic in, headphone out, sockets for 5.1 surround, etc.

I have never had an issue with this as far as output goes and that is all I remember using it for in the past in Ubuntu (and I've had it nearly fifteen years, into Ubuntu for about nine). It has always 'just worked'. Plug it in, switch on the computer, the lights on the eight channels on the outboard audio interface light up, and it's seen in Pulseaudio Volume Control. Plug in some headphones (all I've ever done in Ubuntu) and its that simple. I have used its MIDI sockets, in and out, in both Windows and Ubuntu. Works fine. Everything works fine in Ubuntu, except the inputs on the audio interface which is really what it's all about. :)

The [output from alsa-info is here]("https://paste.ubuntu.com/24227285/").

I can start Jack with no issues and it is set to the correct device. When I look in the connection panel there is nothing in the Audio or MIDI tabs. In the ALSA tab there are the MIDI ports  on device DSP24-1. DSP-1 is selectable in jack Setup> Advanced> input and output device, but DSP-0 is selected as I figured that might be the correct device. Selecting DSP24-1 makes no difference.

I have tweaked endlessly with alsamixer, but all I ever get in Mudita (an app specific to the ICE1712 card) is 'off' for everything, as shown in attached pic. The outputs of the device are switched off, waste of time tweaking them, but I'm wondering if that's off by alsa or Mudita, or the capture section of the device was never switched on by the system in the first place, if that makes sense.

So, bit confused how I should set alsamixer and Mudita (Patchbay/Router) and whether I have them set correctly.

I did remember that in Windows, where the interface works full duplex and capture works fine, the driver was extremely quirky and the 'consumer' card needed to be switched off. Installing the driver for the device did this. I don't use that card, never have, so happy to switch it off. That may remove its sliders from alsamixer and Mudita and make things less confusing. Maybe I could just remove it, but don't remember if it needs to be there for some reason (it is connected to the interface card by a small cable).

I have the internal audio on the MB switched off in BIOS. Any tips, suggestions, ideas, fixes appreciated. I'm hoping this is just my own confusion with the settings or a missing bit of software being installed or loaded at boot. :-k

---

### Post by Bucky Ball on 2017-03-23
Bit confused and increasingly frustrated. I also have an old MBox2 Mini which worked fine on 14.04 LTS. That's a two channel external audio box with USB connection. Sees it fine, but can't get noise out of that on the desktop AV box either. Checking it on my laptop now where it used to work on 14.04. Nothing.

I am obviously missing something and don't know what I'm doing with Linux audio basics. Hopefully the penny will drop shortly as I'm ready to go with the digital audio software. Waste of time learning much more about that if I can't get a noise into the box!

Currently, two external audio devices, both picked up fine by the OS, can't get inputs of either working. Bamboozled. Figuring shouldn't be this tricky and no doubt it isn't. :-k

---

### Post by Bucky Ball on 2017-03-23
Sheesh. Another run around similar to a recent thread about an issue with my old DV camera. Cable. I'd been trying a mic to start, then I plugged a bass in. Tonight I figured maybe one of the cables was dead so tried a different mic cable and worked immediately. Both the previous mic cable and bass instrument cable appear to be dead. My luck. ;)

Anyway, solved and the Mudita settings become more obvious now I can hear what they do. Will post again for further questions/issues as they arise, and there may be a few during my 'Linux audio adventure'.  :)

---

