---
title: "Lost the startup sound"
date: 2010-11-30
forum: Multimedia Software
---

### Post by vesikuusi on 2010-11-30
The startup sound just desappeared. The Gnome Login Sound is still on the list of starting programs and the command is right (/usr/bin/canberra-gtk-play –id=”desktop-login” –description=”GNOME Login”). What makes it more weird is, that it works fine on all other users. I started to suffer from this problem since I tried to change the sound (I have done it before with no problems). At the same time with changing the startup sound I installed PulseAudio volume control. Could these things have something doing with my startup sound desappearence? Thanks! :)

---

### Post by tommcd on 2010-11-30
> **vesikuusi said:**
> The startup sound just desappeared. ... What makes it more weird is, that it works fine on all other users. 
The fact that it works fine for other users likely means that there is something in your user settings that is causing this.
You could try renaming any .gnome files and directories in your home directory to .gnome.bak. Then reboot and see i the problem is fixed.
This will create new and pristine .gnome directories in your home directory. Be aware that this will reset all of your gnome settings to those of a default Ubuntu install.
You can always delete the newly created .gnome directories, and then rename the original .gnome.bak directories back to .gnome if this does not work.

And welcome to the Ubuntu forums!

---

### Post by vesikuusi on 2010-12-01
thanks, I'll try this out as soon as possible :)

---

### Post by lidex on 2010-12-02
> **vesikuusi said:**
> thanks, I'll try this out as soon as possible :)

Or this:
(To remove/reset pulse config)
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by vesikuusi on 2010-12-02
it says, that there's no such file/directory...

---

### Post by vesikuusi on 2010-12-02
renaming directories didn't work either..

---

### Post by lidex on 2010-12-02
> **vesikuusi said:**
> it says, that there's no such file/directory...

That is normal as you may or may not have all of them. Reboot and check your settings in 'Sound Preferences' on the 'Sound Effects' tab.

---

### Post by efflandt on 2010-12-03
In Maverick on my internal hard drive I seem to have lost the login prompt sound, and login sound when gnome starts, a week or so ago when my system updated to kernel 2.6.35-23 and a bunch of other updates.  Possibly related is that if I boot to a (recovery) console and login as myself, **aplay -l** or attempting to use **aplay** to play a sound just hangs until I hit Ctrl+C.  The default sound device should be analog stereo on card 0, device 0.  Sounds in gnome (and console) work fine after gnome starts.

All sounds work fine on essentially the same 64-bit Maverick installed on a USB hard drive, including from a (recovery) console, and all login sounds (and in natty development "installed" on USB flash).  So it is not a hardware issue.

Earlier I had added asla snapshot ppa to also get HDMI sound working for my GT 430 in kernel 2.6.35-22, and login sounds still worked after that until the updates that broke it.  I have since removed the alsa snapshot modules and unchecked those repositories in Synaptic to revert to the standard alsa modules.  I don't need the alsa snapshot for 2.6.35-23 because **aplay -l** lists my HDA NVidia devices and all I needed was the line in /etc/pulse/default.pa to use the right one:

```
load-module module-alsa-sink device=hw:1,9
```With that I can either select Analog Stereo or HDA NVidia for HDMI sound on the fly from Sound Preferences in gnome.  Either work with Rythmbox.

Is there some way to restore asla modules or configuration, so sounds would work in the console shell and login before gnome starts?  I don't have anything configured for asound in ~ or /etc and **rm -r ~/.pulse ~/.pulse-cookie** followed by reboot made no difference.

---

### Post by lidex on 2010-12-03
@efflandt:
Have you checked settings in 'Sound Preferences' on the 'Sound Effects' tab?

---

