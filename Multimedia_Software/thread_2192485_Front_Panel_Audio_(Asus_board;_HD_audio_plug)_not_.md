---
title: "Front Panel Audio (Asus board; HD audio plug) not working"
date: 2013-12-08
forum: Multimedia Software
---

### Post by glen.nelson.1 on 2013-12-08
So my board (ASUS Maximus VI Hero), has the standard front panel microphone and headphone ports. These are hooked up to a 10-1 pin AAFP, using an HD-audio compliment cord. The back ports, which are connected directly work fine, including the headphone port on the back.

UEFI is set to HDAudio for this port, so that isn't the issue. Something I've seen in a thread, but haven't tested, is to set UEFI to AC97. This might be useful for finding the missing device, if it works.

In sound properties, I see three devices:
1. HDMI / DisplayPort 3; This is my graphics cards sound, not an issue.
2. Digital Output (S/PIDF); disabled and not currently used. This is likely the S/PIDF port.
3. Analog Output; This is the back panel, currently set up as 5.1.

alsamixer just displays 1 and 3. Under the Analog Output (which it lists as HDA Intel PCH), it includes a headphones volume which is on, and testing indicates is for the back headphone port. Just in case I turned off auto-mute mode here, but still nothing.

I'm unsure if the front audio panel should appear as a separate audio device, or be part of final device.

I ran the alsa-info script in lindex's signature, since it seemed to commonly help with such issues:
[http://www.alsa-project.org/db/?f=d191215d7a1bf869e1d280af2696c81eea5f38ab](http://www.alsa-project.org/db/?f=d191215d7a1bf869e1d280af2696c81eea5f38ab)

My next step is to try setting the UEFI to AC97, see if it gives me any more hints. Hopefully someone here can speed me along in the right direction.

EDIT:
AC97 created a headphone device, but it doesn't seem to work.

Here is the alsa-info script output with this setup:
[http://www.alsa-project.org/db/?f=7f6e5c95324d654bafda788a7f11c845606061aa](http://www.alsa-project.org/db/?f=7f6e5c95324d654bafda788a7f11c845606061aa)

This has hit the wall of my sound knowledge. More research tomorrow, and hoping someone who knows about this already appears.

---

### Post by Yellow Pasque on 2013-12-08
Maybe this should be set to true?
```
	control.43 {
		iface CARD
		name 'Front Headphone Jack'
		value false  <-----------------
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}

```
The first thing I'd suggest is using latest driver to make sure this is not already fixed upstream: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If that still doesn't work after reboot, then I'd suggest filing a bug using command 'ubuntu-bug audio' as there are a couple people who are very good at dealing with pins/verbs and producing driver-level fixes.

EDIT: please set your UEFI to HDA before doing any of that.

---

### Post by glen.nelson.1 on 2013-12-08
Thanks for the advice Temüjin!

I'll give the upgrade a shot, and I have it set back to HDA. I will report back results, and include a link to the bug, if any, in this post in case it helps anyone else.

---

### Post by glen.nelson.1 on 2013-12-08
Unfortunately, the upgrade did not work. A [bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1259013") has been submitted.

---

### Post by glen.nelson.1 on 2013-12-09
A final update in case anyone finds this:

I had a problem with either the HDAudio cable not fully plugged in, or my case was badly wired and because a front fan connection circuit wasn't completed (LED switch -> fan, fan wasn't powered on, due to needing a longer fan cable.)

---

