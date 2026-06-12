---
title: "video driver help"
date: 2013-09-26
forum: Multimedia Software
---

### Post by Xbmrdbx on 2013-09-26
I'm running Xubuntu 13.04 on a celeron g1610 ivy bridge. I'm using VLC 2.0.8 got blu-ray working but it is looks terrible blocking and some odd looking smearing going on. DVD playback is much better but bad tearing during action scenes. What do i need to do to get this looking better? Also i see something for intel processor micro code in the software center do i need that?

---

### Post by Bucky Ball on 2013-09-26
*Thread moved to **Multimedia & Video**.*

Welcome. Try installing xubuntu-restricted-extras from Synaptic Package Manager. Reboot.

It would help if you told us what video card you are using and what driver, if you know ...

If you open 'Additional Drivers' is there anything there disabled?

---

### Post by Yellow Pasque on 2013-09-27
I'm assuming it's the video integrated into the G1610 (Intel HD2500 graphics). (If not, give info BB asked for.)

Does this only happen in VLC? Have you tried other video players?

---

### Post by Xbmrdbx on 2013-09-28
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

Welcome. Try installing xubuntu-restricted-extras from Synaptic Package Manager. Reboot.

It would help if you told us what video card you are using and what driver, if you know ...

If you open 'Additional Drivers' is there anything there disabled?
Xubuntu-restricted-extras installed according to software center. How do you get to Synaptic package manager in Xubuntu? No video card using  integrated video. No video driver has been installed. Settings>software & updates>additional drivers is empty (no proprietary drivers are in use).

[quote=Temüjin]Does this only happen in VLC? Have you tried other video players? 		[/quote]

VLC is the only thing i added Parole was installed with the distro. Parole media player will not open blu-ray but dvd playback is even worst on parole.

---

### Post by Bucky Ball on 2013-09-28
Apps>System>Synaptics. Don't know if it's installed by default (I use a customised mini.iso install so don't use Software Centre, only Synaptics - SCentre fine though, same really). ;)

---

### Post by Xbmrdbx on 2013-10-24
> **Bucky Ball said:**
> Apps>System>Synaptics. Don't know if it's installed by default (I use a customised mini.iso install so don't use Software Centre, only Synaptics - SCentre fine though, same really). ;)
Synaptics not installed as far as i can tell. Can't anyone help with this ? Anyone out there using buntu for blu-ray playback ?

---

### Post by Bucky Ball on 2013-10-24
Well, install xubuntu-restricted-extras through Software Centre, then. Same-same pretty much.

PS: You have been absent for three weeks so no, not much attention paid to inactive threads. ;)

PPS: Synaptics must no longer be installed by default then as it is in 12.04 LTS. Anyway ...

---

### Post by Yellow Pasque on 2013-10-25
> No video driver has been installed.
The open-source intel driver is installed by default.

I solved my video tearing issue by turning off the compositor built into xfce and using compton compositor, but that may be a bit advanced for most users.

---

