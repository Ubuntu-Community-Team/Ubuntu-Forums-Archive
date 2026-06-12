---
title: "HDMI audio using VT1708s chipset ?"
date: 2010-07-05
forum: Multimedia Software
---

### Post by kaband on 2010-07-05
Ok, so let me first start off by saying I'm a linux noob.  I feel no shame. :)

I've been working on trying to solve my issue for a few days now and after much research I am still no better off.  But I am able to at least narrow down my problem.

The long and short of it is that my HDMI audio device is not showing up in Ubuntu 10.4 x64 edition.  Let me give a few specs.

Motherboard: ASROCK 785GMH/128
Onboard video: ATI Radeon HD 4200
Onboard audio: VIA® VT1708S
OS: Ubuntu 10.4 x64
Alsa drivers: alsa-driver-1.0.23
ATI Drivers: ATI Catalyst 10.6

Running the latest version of ALSA and ATI's proprietary linux drivers.

I can see all outputs (including the s/pdif) except the HDMI.  From my reading there should be a device listed on a 2nd card called ATI HDA HDMI

aplay -l returns the following result:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The HDMI card and device are not being found, but the hardware is physically there.  Again, from research there should be an additional card listed, like this:

card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

Now, the questions:

1. Has anyone been able to get the HDA ATI HDMI card to show up w. the VIA 1708s chipset using ubuntu 10.4 x64?  If so, how did you get it to show?

2. Do the alsa drivers even support it?

3. Can anyone make a recommendation of a soundcard which will work, so I can get audio out of my HDMI Port?

I'm hoping someone out there can give me some guidance.  Thanks so much.

Justin

---

### Post by kaband on 2010-07-05
Update:

Ok, shortly after I posted this I figured out my issue.  Wanna know what the fix was?  The freaking onboard hdmi audio was disabled in the BIOS by default.  Once I enabled the the onboard hdmi audio ubuntu 10.4 found it with no problem.

Now my next issue will be to figure out why I am getting choppy or static sound when using the HDMI audio in XBMC.  If anyone, has any advice . . . please let me know.  :)

I hope this helps someone who had the same issue as I did.  I worked very hard to try and resolve this issue only to find out that it was just a BIOS change.  Oh well, I learned a whole lot through the process, so it wasnt a total loss.

---

