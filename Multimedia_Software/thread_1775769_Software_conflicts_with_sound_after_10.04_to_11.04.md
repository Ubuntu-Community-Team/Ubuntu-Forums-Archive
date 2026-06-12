---
title: "Software conflicts with sound after 10.04 to 11.04 upgrade"
date: 2011-06-05
forum: Multimedia Software
---

### Post by .broken. on 2011-06-05
Hello everyone,

I've come here after 3 hours of googling and editing of settings. I'd really appreciate some help before I bugger things up further!

First off, aplay -l didn't return a soundcard so I loaded the appropriate module in /etc/modules.

Flash, Rhythmbox and VLC worked (at least, so I thought) and I managed to get Spotify to work with the following solution [http://ubuntuforums.org/showpost.php?p=10293820&postcount=8](http://ubuntuforums.org/showpost.php?p=10293820&postcount=8). Skype wasn't working though :(

I then noticed that Flash wasn't working after running Rhythmbox so used the Flash-aid Firefox extension to fix video issues and this ([http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)) in an attempt to solve the different programs hogging the sound.

I was hoping to fix Skype after sorting this out.

One reboot later and now nothing works except Flash!

- Spotify: doesn't work under either ALSA or OSS options. Also, the wave-out device appears to be missing from the ALSA list in Wine Config.
- VLC: doesn't work under either ALSA or PulseAudio settings.
- Skype: can only select PulseAudio Server and doesn't work (de-selected the automatic adjustment option as per recommendation somewhere during my time googling).
- Rhythmbox: can't find any sound output options.

I'd be really grateful if someone could guide me through how to fix this.

Many thanks,
James

---

### Post by .broken. on 2011-06-05
Right, so I changed the settings in gstreamer-properties and edited the volume control output and now everything seems to be working!

Still can't have more than one program using the sound at any one time though. Can someone please help?

Many thanks,
James

---

### Post by wadedesk on 2011-06-05
I have a Toshiba Satellite 665 laptop and I lost the sound input after upgrading to Ubuntu 11.04.  This means that I can not use Skype to make phone calls any longer.  When I boot into Gnome desktop, the sound is distorted but ends up smoothing out after the desktop is completely loaded.

When I go into Sound Preferences it seems to recognise VLC, Radio Tray and other sound programs work with the exception of Skype.  Skype does not show up at all in Sound Preferences, so I can not adjust output level.  I can hear sound on Echo test.

Sound Preferences does not recognise the input jack, built-in microphone, nor HD Logitech webcam microphone over usb.  Video does work.

Ubuntu Maveric 10.10 would not boot so I had to disable ACPI on start-up.  That is fixed in Natty 11.04, but lack of sound input is a much larger issue.

---

### Post by wadedesk on 2011-06-16
I previously posted that my sound input is not working on Ubuntu 11.04 64-bit OS running on a Toshiba A665.  I've since installed Ubuntu 11.04 32-bit OS on a Compaq NVO N600c PIII laptop.  The sound input does not work on it either.

One difference in the Compaq install from the Toshiba install is that Skype input and output does show up in Sound Preferences on the Compaq 32-bit install.  I had Ubuntu 10.10 previously installed on the Compaq with no problems with the sound input or Skype program function.

I've also tried a 32-bit Skype install in a VMware Player running Windows XP on the Toshiba 64-bit 11.04 installation.  This VMware Windows XP Professional ran perfectly in Ubuntu 10.10.  However when I try to launch Skype in VMware on the 11.04 Ubuntu Host, it now crashes.

It appears to me the problem with sound recording my be with the current Kernal.

I hope if more people report this problem that it will be addressed.

---

### Post by lidex on 2011-06-18
> **wadedesk said:**
> I previously posted that my sound input is not working on Ubuntu 11.04 64-bit OS running on a Toshiba A665.  I've since installed Ubuntu 11.04 32-bit OS on a Compaq NVO N600c PIII laptop.  The sound input does not work on it either.

One difference in the Compaq install from the Toshiba install is that Skype input and output does show up in Sound Preferences on the Compaq 32-bit install.  I had Ubuntu 10.10 previously installed on the Compaq with no problems with the sound input or Skype program function.

I've also tried a 32-bit Skype install in a VMware Player running Windows XP on the Toshiba 64-bit 11.04 installation.  This VMware Windows XP Professional ran perfectly in Ubuntu 10.10.  However when I try to launch Skype in VMware on the 11.04 Ubuntu Host, it now crashes.

It appears to me the problem with sound recording my be with the current Kernal.

I hope if more people report this problem that it will be addressed.

Asking for help in the forums is not the same as reporting the problem. You need to file a bug. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by wadedesk on 2011-06-20
I had previously reported problems with non-working audio inputs for the internal mic, audio jace, and webcam mic via USB.  In the last 24 hours the bugs on both the Toshiba 64-bit 4-core and Compac PIII systems corrected themselves by daily update.  What ever the issue was that I had, has been resolved.

---

### Post by DAB4970 on 2011-06-25
How did each of you do the upgrades?  Internet upgrade or clean install from CD-rom?
I've seen and been told that clean installs are the best route to go when upgrading.

---

### Post by lidex on 2011-06-26
> **DAB4970 said:**
> How did each of you do the upgrades?  Internet upgrade or clean install from CD-rom?
I've seen and been told that clean installs are the best route to go when upgrading.

He was referring to updating, not upgrading. Number of ways to do that. Try this:
```
sudo apt-get update && sudo apt-get upgrade
```
I know it says upgrade but it's not a distribution upgrade, you're basically updating/upgrading some packages. Probably a bug-fix update came across.

---

