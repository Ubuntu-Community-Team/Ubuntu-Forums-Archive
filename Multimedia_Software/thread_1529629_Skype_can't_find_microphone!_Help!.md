---
title: "Skype can't find microphone! Help!"
date: 2010-07-12
forum: Multimedia Software
---

### Post by quixote on 2010-07-12
This is driving me nuts.  (Nuts!)  Everything works outside of Skype.  Speakers work in Skype, but the microphone stays dead.  I've dumped Pulseaudio, made sure volume is up in Alsa, rebooted, but Skype still lists Pulseaudio as what it's using!  How do I get its tiny mind to use something else??????

There was also a thread saying an earlier version of Skype, 2.1.0.47, used to work, but I can't find a 64-bit version of that.  I've got the 32-bit version which I could run in a 32-bit ubuntu in virtualbox, but fergawdssake there has to be a better way!

How do I make sure the system isn't still somehow using Pulseaudio?  I did purge it.  It should be gone.

Output of various system specs:```

**uname -a**
Linux bunty 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**dpkg -l | grep "alsa"**
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                                   ALSA driver configuration files
ii  alsa-oss                              1.0.17-3                                                 ALSA wrapper for OSS applications
ii  alsa-tools                            1.0.22-0ubuntu1                                          Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                        1.0.22-0ubuntu1                                          GUI based ALSA utilities for specific hardware
ii  alsa-utils                            1.0.22-0ubuntu5                                          ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                            Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                                ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                                GStreamer plugin for ALSA
ii  libesd-alsa0                          0.2.41-6ubuntu1                                          Enlightened Sound Daemon (ALSA) - transitional package
rc  libsdl1.2debian-alsa                  1.2.13-4ubuntu4                                          Simple DirectMedia Layer (with X11 and ALSA options)
ii  zoiper-communicator-free-alsa         1.0-1ubuntu12                                            SIP/IAX phone with presence and instant messaging support

**dpkg -l | grep "pulse"**
ii  gstreamer0.10-pulseaudio              0.10.21-1ubuntu3                                         GStreamer plugin for PulseAudio
ii  libpulse-browse0                      1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14          PulseAudio client libraries (zeroconf support)
ii  libpulse-dev                          1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14          PulseAudio client development headers and libraries
ii  libpulse-mainloop-glib0               1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14          PulseAudio client libraries (glib support)
ii  libpulse0                             1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14          PulseAudio client libraries
ii  libsdl1.2debian-pulseaudio            1.2.14-4ubuntu1.1                                        Simple DirectMedia Layer (with X11 and PulseAudio options)
ii  pulseaudio                            1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14          PulseAudio sound server
ii  pulseaudio-utils                      1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14          Command line tools for the PulseAudio sound server
ii  vlc-plugin-pulse                      1.0.6-1ubuntu1.1                                         PulseAudio plugin for VLC


:~$ **head -n 1 /proc/asound/card*/codec#***
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5069

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX


```

---

### Post by quixote on 2010-07-12
Still fussing about.  I went to System > Preferences > Sound one more time, and under the Input tab my sound device was no longer selected.  I have no idea what deselected it, except I'm pretty sure it wasn't me.  I selected it again, turned up the volume some more and now . . . 

the microphone in Skype finally works.  :shock:  Oh, and Skype still says it's using Pulseaudio, for what it's worth.

Is this just a fluke?  Will it now keep working?  (Mind you, it sounds awful, but that's a separate issue.)  Will it turn itself off again?  How do I make sure this is permanent?

---

### Post by lidex on 2010-07-14
See this thread:
[http://ubuntuforums.org/showthread.php?t=1516071]("http://ubuntuforums.org/showthread.php?t=1516071")

What is the make/model of your pc?

---

### Post by quixote on 2010-07-14
(So busy with details, I kind of forgot the big one ... :redface:) My machine is a Thinkpad X201s.

I saw the thread earlier that you linked.  It's very helpful.  That's how I found out how to unmute the mic to begin with.  Rather bizarre that the default sound preferences GUI lets you twiddle the slider bar to turn the volume up, but forgets to let you know that's not going to do anything!

---

### Post by lidex on 2010-07-14
Damn, asleep at the wheel. Try these audio drivers for conexant chips. You'll need to select the correct one for download:
[http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

---

### Post by quixote on 2010-07-15
Do the x201s have conexant chips?  I have no idea what they have. ... Oh, wait, I just read my own box above and I do see "conexant."  Whaddya know!  I had no idea what that mean or that there were special drivers.  I find the instructions on that site intimidating (I'm always intimidated by stuff that operates on the kernel), but I'll give it a try and report back.  Wish me luck! :biggrin:

---

### Post by lidex on 2010-07-15
Good Luck!

---

### Post by quixote on 2010-07-16
Hmm.  Not so good.  The installation went without a hitch.  I used  	alsa-driver-linuxant_1.0.23.0_all.deb.zip because I have 64-bit system and a more recent kernel than the pre-compiled packages support.  I checked for gcc & make, both there, so that was fine.

But then when I rebooted, it stopped during shutdown at "shutting down sound".  (It said a lot more than that, but that was the last line and the only one I remember.) I did a hard reset, and when it came back up, there was no way to access sound.  "alsamixer" in a terminal didn't work, and Preferences > Sound wouldn't load.  So I uninstalled alsa-linuxant using synaptic and told it to "completely uninstall" including config files.

That may have been a mistake.  It still didn't want to shut down normally, although it wasn't hung up on sound this time. I did another hard reset, and when it came up, it's lost all track of my sound card.  Under Prefs > Sound, it shows using "Dummy output" for instance.

One thing I noticed but didn't really think about at the time is that my installed alsa is 1.0.22, but also-linuxant was 1.0.23.  Could that have been the problem?  Should I move up to also 1.0.23?  And if so, is there a ppa, so I don't have to keep updating it by hand?

I don't remember, or I never knew, how do I tell the system about my sound card?  I'm feeling all :confused:

---

### Post by lidex on 2010-07-17
> **quixote said:**
> Hmm.  Not so good.  The installation went without a hitch.  I used  	alsa-driver-linuxant_1.0.23.0_all.deb.zip because I have 64-bit system and a more recent kernel than the pre-compiled packages support.  I checked for gcc & make, both there, so that was fine.

But then when I rebooted, it stopped during shutdown at "shutting down sound".  (It said a lot more than that, but that was the last line and the only one I remember.) I did a hard reset, and when it came back up, there was no way to access sound.  "alsamixer" in a terminal didn't work, and Preferences > Sound wouldn't load.  So I uninstalled alsa-linuxant using synaptic and told it to "completely uninstall" including config files.

That may have been a mistake.  It still didn't want to shut down normally, although it wasn't hung up on sound this time. I did another hard reset, and when it came up, it's lost all track of my sound card.  Under Prefs > Sound, it shows using "Dummy output" for instance.

One thing I noticed but didn't really think about at the time is that my installed alsa is 1.0.22, but also-linuxant was 1.0.23.  Could that have been the problem?  Should I move up to also 1.0.23?  And if so, is there a ppa, so I don't have to keep updating it by hand?

I don't remember, or I never knew, how do I tell the system about my sound card?  I'm feeling all :confused:

Hmm, yeah, not good. Something went wrong although not sure what. Did/do you have any alsa backports installed? If so remove them. Try this to get back to base configuration: Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

### Post by quixote on 2010-07-17
I tried reinstalling linux-sound-base, alsa-base, alsa-utils but it's still not seeing my sound card.  It's a bog-standard Intel card so I tried looking up the standard way of making the system see the sound card, but this is what I get: ```
$**lspci -v** 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Lenovo Device 215e
	Flags: fast devsel, IRQ 11
	Memory at f2520000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

$**sudo modprobe snd-hda-intel**
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.32-23-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

the first few lines of
$**dmesg | grep 'snd'**
[   18.424315] thinkpad_acpi: disagrees about version of symbol snd_ctl_add
[   18.424319] thinkpad_acpi: Unknown symbol snd_ctl_add
[   18.424562] thinkpad_acpi: disagrees about version of symbol snd_card_register
[   18.424565] thinkpad_acpi: Unknown symbol snd_card_register
[   18.424674] thinkpad_acpi: disagrees about version of symbol snd_card_free
[   18.424677] thinkpad_acpi: Unknown symbol snd_card_free

and so on for nearly a hundred more lines

```

So ubuntu does know there's a sound card, but the kernel module blew up or something? ??  aplay -l lists "no soundcard", likewise /proc/asound/card*/codec#*.  Is there some way to rebuild or download a working sound kernel module for snd-hda-intel?  Or isn't that really the problem?

---

### Post by quixote on 2010-07-17
Forgot to answer re backports: as far as I can tell, no, none installed.  I searched for "backports" in synaptic, and there's quite a number with "alsa" in the name, but none of them are installed.

Update a bit later:  I tried adding this line to the end of /etc/modprobe.d/alsa-base.conf:```
options snd-hda-intel model=thinkpad
``` but that changes nothing.  Likewise with model=lenovo.  (I should mention, I do reboot between attempts, so the changes should take effect, if they're going to.)

---

### Post by lidex on 2010-07-18
Try re-installing kernel headers. Not sure of the command so use synaptic.

---

### Post by quixote on 2010-07-18
This is getting weirder and weirder.  Reinstalling the header didn't solve the problem, but I figured if it's a kernel problem, maybe I should boot into one of my older kernels.  Sound works in 2.6.32.22!   So then I tried reinstalling all three kernel files for 32.23 (the one I was using when I tried the linuxant version), image, header, and header-generic, but still refuses to see the sound card.  Very strange.  I guess I could just uninstall 32.23, and see if an update-manager update is more effective.

One odd thing: when I was in the older kernel I opened alsamixer from the terminal, unmuted S/PDIF (I don't even know what that does), upped the volume on a couple of things, and exited.  Then I ran "sudo alsactl store 0" to store the settings and got the error? warning? "/home/quixote is not ours".

??  I haven't seen that before.  I also don't see any ~/.alsa* ~/.pulse* ~/.sound or anything similar, either files or dirs, it could be trying to write to.  So what's that all about?  Could it be that the linuxant alsa version changed the permissions on some obscure file and that's what's causing the problem?

---

### Post by lidex on 2010-07-18
More likely the issue was present before and causing the problem. Do you log in as root?

Maybe try booting into next-to-latest kernel, completely remove newest kernel and header packages, then this:
```
sudo apt-get update
sudo apt-get upgrade
```
**Reboot**

---

### Post by quixote on 2010-07-18
No, I never login as root.  The problem wasn't present before the attempt with the linuxant alsa install.  I'm sure of that because the whole thing started with me trying to get Skype working, so I know the speakers, mic, all both internal and external, were all functioning.  As I mentioned, the problem with the mic turned out to be that it was muted somewhere way down in the bowels of the system and only alsamixer started from the command line actually dealt with that.  Playback from the mic input sounded awful though, and the idea with trying the conexant-alsa was to fix that.  So this is definitely some weirdness associated with either the linuxant-alsa install or with uninstalling it using a complete purge.

I'll try completely removing the 32.23 kernel and then using update.  

(By the way, brain hiccup in my previous comment: of course there's a .pulse dir in my ~/ ...)

---

### Post by quixote on 2010-07-22
Since I removed the 32.23 kernel manually, the system seems to be assuming I don't want it and is not offering it in the upgrade.  Frustrating!  If I just reinstall it again via Synaptic, I still have the no sound issue.  

I've just been booting into the 32.22 kernel.  But I'm still mystified how a driver could so totally change a kernel that even when you remove it, the problem remains.  It's like magic.  Hopefully, the next kernel upgrade will make it magically go away! :D

---

### Post by lidex on 2010-07-23
Probably a good thing. That kernel was causing problems so stay away from it.
What is your audio status now?

---

### Post by quixote on 2010-07-23
Sound works fine under the older kernel.  And hopefully will again when the next new kernel shows up.  From the perspective of using the system, there's zero difference between the two kernel versions for me, so it doesn't matter either way. All's well that ends well. :D

---

