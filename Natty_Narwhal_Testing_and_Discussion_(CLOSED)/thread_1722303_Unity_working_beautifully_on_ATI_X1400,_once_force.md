---
title: "Unity working beautifully on ATI X1400, once forced"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JPorter on 2011-04-05
I've had some frustration with the poor "default" state of graphics output on Natty when using older ATI graphics hardware, but once I forced it to turn on KMS and 3D support, which auto-enabled compiz, it's working beautifully with full acceleration.  My chip is a Mobility X1400, which is an RV515 core. This is on a Thinkpad T60 laptop.

I kept getting "KMS not supported" errors in dmesg and Xorg.0.log, so I decided to force it on since I've used KMS and compiz in the past without issues.

What I had to do:
[INDENT]Update to latest packages from xorg-edgers PPA
Force ia32-libs to version from xorg-edgers PPA
Install ia32-libs-mesa-dri-experimental from xorg-edgers PPA
Pre-load radeon module by adding[FONT="Courier New"] radeon [/FONT]to /etc/modules
Turn on KMS by adding[FONT="Courier New"] options radeon modeset=1 [/FONT]to a new conf file in /etc/modprobe.d
Run[FONT="Courier New"] sudo update-initramfs -u [/FONT]and then reboot.[/INDENT]

Now I have a full Unity 3D desktop, with KMS running perfectly along with Gallium3D enabled Mesa.  Display output is excellent.  Flash video is flicker-free, even in full screen.

I understand that some of these packages are considered "experimental", but the function is far superior to the current defaults.  What are the chances of some of this being turned on by default prior to the Natty launch?

---

### Post by clhsharky on 2011-04-05
JPorter

> Now I have a full Unity 3D desktop, with KMS running perfectly along with Gallium3D enabled Mesa. Display output is excellent. Flash video is flicker-free, even in full screen.
I also on a default install of Natty + restricted-extras.
> What are the chances of some of this being turned on by default prior to the Natty launch? 
KMS and Gallium3D are already.
Don't know why yours didn't.
How did you install Natty, upgrade or fresh?

My chip is a ATI Radeon X1650 (RV520).
I do use edgers on my 10.04 and 10.10 installs(same machine)but not using them on Natty.


Sharky

---

### Post by JPorter on 2011-04-05
> **clhsharky said:**
> KMS and Gallium3D are already.
Don't know why yours didn't.
How did you install Natty, upgrade or fresh?

Sharky

Fresh Natty 64 install from the nightly, using the alternate CD image. Maybe it's something to do with the alternate install, versus the Desktop image?

Default behavior dropped me directly to Ubuntu Classic (no effects) after telling me that my hardware was incompatible.

Maybe it was a transient bug in the nightly, I don't know... but I'm seeing an awful lot of people on here with ATI cards complaining about not being able to run Unity, and most of them have much newer graphics hardware than I do.

---

### Post by cariboo on 2011-04-05
> **JPorter said:**
> I've had some frustration with the poor "default" state of graphics output on Natty when using older ATI graphics hardware, but once I forced it to turn on KMS and 3D support, which auto-enabled compiz, it's working beautifully with full acceleration.  My chip is a Mobility X1400, which is an RV515 core. This is on a Thinkpad T60 laptop.

I kept getting "KMS not supported" errors in dmesg and Xorg.0.log, so I decided to force it on since I've used KMS and compiz in the past without issues.

What I had to do:
[INDENT]Update to latest packages from xorg-edgers PPA
Force ia32-libs to version from xorg-edgers PPA
Install ia32-libs-mesa-dri-experimental from xorg-edgers PPA
Pre-load radeon module by adding[FONT="Courier New"] radeon [/FONT]to /etc/modules
Turn on KMS by adding[FONT="Courier New"] options radeon modeset=1 [/FONT]to a new conf file in /etc/modprobe.d
Run[FONT="Courier New"] sudo update-initramfs -u [/FONT]and then reboot.[/INDENT]

Now I have a full Unity 3D desktop, with KMS running perfectly along with Gallium3D enabled Mesa.  Display output is excellent.  Flash video is flicker-free, even in full screen.

I understand that some of these packages are considered "experimental", but the function is far superior to the current defaults.  What are the chances of some of this being turned on by default prior to the Natty launch?

They chances of anything new being added before the Natty release, are slim to none, as there was a feature freeze on Feb 24th, a UI freeze on March 24th, and a Final Freeze on the 14th of this month. The final freeze means that nothing will be added after that date. The final to weeks leading up to release are for bug fixing only.

> Maybe it was a transient bug in the nightly, I don't know... but I'm seeing an awful lot of people on here with ATI cards complaining about not being able to run Unity, and most of them have much newer graphics hardware than I do.

I would suggest that most of the people having problems with the closed source ATI driver didn't read the instructions or release notes on how to properly install it.

---

### Post by JPorter on 2011-04-05
> **cariboo907 said:**
> I would suggest that most of the people having problems with the closed source ATI driver didn't read the instructions or release notes on how to properly install it.

Not the closed source (fglrx) driver.  The open source (radeon) driver, which is default.  I can make a list of threads reporting this exact issue if you'd like... it seems there are a ton of people with recent ATI cards that are Unity-unsupported by default, which shouldn't be the case based on the current state of the open-source ATI drivers.

I can try re-installing from scratch using the 32-bit Desktop ISO and 64-bit Desktop ISO to see if the behavior changes, if you think it would do any good?

---

### Post by matros_ua on 2011-04-13
> **JPorter said:**
> [INDENT]Update to latest packages from xorg-edgers PPA
Force ia32-libs to version from xorg-edgers PPA
Install ia32-libs-mesa-dri-experimental from xorg-edgers PPA
Pre-load radeon module by adding[FONT=Courier New] radeon [/FONT]to /etc/modules
Turn on KMS by adding[FONT=Courier New] options radeon modeset=1 [/FONT]to a new conf file in /etc/modprobe.d
Run[FONT=Courier New] sudo update-initramfs -u [/FONT]and then reboot.[/INDENT]

Hi, I'm newer here. Can You explain step-by-step How did You do that?

I have Notebook dell 6400 with Ati X1400, Ubuntu 11.04 and dual monitor (additional is Dell 17")

When the Ubuntu has been installed I got Unity with two monitor but with wrong rosolution. When I try to change settings in xorg.conf I can get correct resolution but Ubuntu don't want to load Unity.

Pls help!!

---

### Post by JPorter on 2011-04-18
> **matros_ua said:**
> Hi, I'm newer here. Can You explain step-by-step How did You do that?

I have Notebook dell 6400 with Ati X1400, Ubuntu 11.04 and dual monitor (additional is Dell 17")

When the Ubuntu has been installed I got Unity with two monitor but with wrong rosolution. When I try to change settings in xorg.conf I can get correct resolution but Ubuntu don't want to load Unity.

Pls help!!

I'm not sure which party you're having difficulty with.  It wounds like you are getting KMS and Unity working by default out of the box, which wasn't the case with mine.

The multi-monitor issues aren't related to that. Usually you can configure the monitors directly through the Monitors panel in System Preferences, rather than using xorg.conf.  Have you tried that at all?

If your monitors aren't being detected correctly, leading to the wrong-resolution behavior, it may be an EDID issue with the specific monitor.

More info would be helpful.

---

### Post by screaminj3sus on 2011-04-20
> **JPorter said:**
> I've had some frustration with the poor "default" state of graphics output on Natty when using older ATI graphics hardware, but once I forced it to turn on KMS and 3D support, which auto-enabled compiz, it's working beautifully with full acceleration.  My chip is a Mobility X1400, which is an RV515 core. This is on a Thinkpad T60 laptop.

I kept getting "KMS not supported" errors in dmesg and Xorg.0.log, so I decided to force it on since I've used KMS and compiz in the past without issues.

What I had to do:
[INDENT]Update to latest packages from xorg-edgers PPA
Force ia32-libs to version from xorg-edgers PPA
Install ia32-libs-mesa-dri-experimental from xorg-edgers PPA
Pre-load radeon module by adding[FONT="Courier New"] radeon [/FONT]to /etc/modules
Turn on KMS by adding[FONT="Courier New"] options radeon modeset=1 [/FONT]to a new conf file in /etc/modprobe.d
Run[FONT="Courier New"] sudo update-initramfs -u [/FONT]and then reboot.[/INDENT]

Now I have a full Unity 3D desktop, with KMS running perfectly along with Gallium3D enabled Mesa.  Display output is excellent.  Flash video is flicker-free, even in full screen.

I understand that some of these packages are considered "experimental", but the function is far superior to the current defaults.  What are the chances of some of this being turned on by default prior to the Natty launch?

All that should have been working with your card out of the box. Seems like a bug that it didn't.

---

### Post by gyaneshwar on 2011-04-26
Hi there,

I have a problem with dual monitor setup on Natty. 

I am using X1650 and in all modes except Gnome safe mode I can not get second monitor to rotate 90 degrees.

On Unity even icon line moves to the second monitor.

I did fresh install.

Any ideas which are not too complicated.

Thanks

sgy

---

