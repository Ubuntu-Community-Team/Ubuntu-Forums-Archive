---
title: "HOWTO: Help for HDA Intel/ALC888 &amp; No Sound on Jaunty 9.04"
date: 2009-05-08
forum: Multimedia Software
---

### Post by wyth on 2009-05-08
[COLOR=Blue]***NOTE: I had made this work through a release candidate kernel, but experienced other problems, and then found a better way.  This page is edited to reflect what works without messing with the kernel, but the kernel options are included below if you want to give it a try.***[/COLOR]

After a clean install of 9.04, I completely nixed my sound.  There are bugs galore on this, and the variations are too wide to name them here -- just search launchpad for [HDA Intel]("https://launchpad.net/+search?field.text=HDA+Intel+jaunty&field.actions.search=Search") or [ALC888 issues]("https://launchpad.net/+search?field.text=ALC888+jaunty&field.actions.search=Search") in Jaunty.

I got mine to work.  Here's how.

My specs: 

[LIST]
[*]Intel 82801I (ICH9 Family) HD Audio Controller (rev 02) -- a Realtek ALC888
[*]nVidia GeForce 8600 GT GFX,
[*]Intel Dual CPU E2160,
[*]all on a Dell Insprion 530 (bought with Ubuntu installed).
[/LIST]

**First**, Go to System > Preferences > Sound and set the options to Autodetect, except Sound Catcher (ALSA) and Default Mixer Tracks (HDA Intel)
[B]
Second, [/B]Open the PulseAudio Device Chooser, and in there make sure the Output tab has your card set as default. (Right-click on the name of the card, or the dropdown on the right side of that part of the tab where  you can set 'default'.)  

Then open some program that'll play audio and play something.  Check the Playback tab of the Volume Control and see if it shows it's playing.  If you're not getting any sound but pulse clearly shows it's getting the stream, move to the Configuration tab and look for the Profile dropdown under HDA Intel.  Mine was set for Output digital, which gave me nothing.  Output Analog gave me fine sound.


[LEFT]**[COLOR=Blue]***** IF THOSE DON'T WORK *****[/COLOR]**
[/LEFT]

**Third**, Try grabbing the latest ALSA from from [Luke Yelavich's launchpad PPA]("https://launchpad.net/%7Ethemuso/+archive/ppa").  Luke is a [Canonical employee who works on accessibility issues]("https://wiki.ubuntu.com/LukeYelavich").  You might not need the latest package, but this is where I ended up after trying a shotgun approach, and now it's working.

**Fourth,** Open /etc/modprobe.d/alsa-base.conf. with your favorite editor and add an option  (*it has to be your favorite editor; it won't work if you use your second-favorite editor or your least-favorite editor*).  Here's what I added at the end:

```
options snd-hda-intel model=6stack-dig
```The snd-hda-intel needs to be added, and there are a number of different model options available.  The one I used is for a Dell.  

To find your model, check in 
/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz
Open the ALSA-Configuration.txt inside the tar.gz and look for your model, like ALC888 -- find that with ```
aplay -l
```A safe model one to start with, if you're not sure, is model=auto; that uses the BIOS default.  Note that in the ALSA-Configuration file, about every entry is double-titled, like ALC883/888, so if you do a search for ALC888 you'll come up blank.


**[COLOR=Blue] ***** FURTHERMORE *****[/COLOR]**

If you're still having some issues, a couple of other things to try in /etc/modprobe.d/alsa-base.conf are:
```
options snd-hda-intel probe_mask=1
```or
```
options snd-hda-intel probe_mask=8
```**Note: **That would replace 
```
options snd-hda-intel model=6stack-dig
```If you're using PulseAudio and get the crackly, distorted sound, you can also try the following ([from this thread]("http://ubuntuforums.org/showthread.php?t=789578")):

Open (as root) /etc/pulse/daemon.conf with your favorite editor.

Find the following lines in the file, and change the numbers to what's below:
```
default-fragments = 8
default-fragment-size-msec = 10

```[B][COLOR=Blue]

***** OBSOLETE *****[/COLOR][/B]

I had tried the 2.6.30-rc4-generic kernel.  I gave this a try because my laptop was bit by the [Intel graphics bug]("http://ubuntuforums.org/showthread.php?t=1130582"), and using that kernel helped. I can report that before I caught the Output analog thing with Pulse, I had tried a number of different snd-hda-intel models, and even with the newest ALSA from the PPA, I still had absolutely no sound except for headphones

The rc4 of 2.6.30-generic did the trick, but my gfx performance degraded. And honeslty, I had to constantly tweak some pulse settings to keep it from stuttering. Going back to the 2.6.28-12-generic kernel with the right Configuration set in Pulse worked fine. 

If you want to toy with the release candidate kernel, here's how to get it from the [Ubuntu Kernel Team's repository]("https://launchpad.net/%7Eubuntu-kernel-team") (note their PPA isn't open for adding to your sources.list, but the files can be downloaded):

```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-headers-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-headers-2.6.30-020630rc4_2.6.30-020630rc4_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb 
```[B]
Note:[/B] If you check [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") first, you can find the latest kernel and replace the .deb file names in the above code with whatever you want to try.

Then to install:
```
sudo dpkg -i linux-headers-2.6.30-020630rc4_2.6.30-020630rc4_all.deb linux-headers-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb
```With those settings, my sound came back in full force, loud and clear and beautiful. This *may* only work for my specific hardware configuration, and I just got lucky, but if you're soundless, you might want to give this a try.

***EDIT:*** I almost forgot -- In my set-up, I had to turn on the Side switch in the Volume Control Preferences (right-click the Gnome Volume Applet > Open Volume Control). 

***EDIT: ***I just got all the updates to the 2.6.28-12-generic kernel, and I'm going to reboot into that and see if it still works.

---

### Post by Spaced on 2009-05-14
Although I don't have the same card as you (mine is an Intel 82801H [ICH8 Family]), I'm trying if your solutions work for me... for the moment I've tried the first step, I did everything as you suggest and nothing changed. 
If this can help, when I move the volume control in padevchooser I see these messages appearing repeatedly in the terminal window:

**[For my "Hardware Output device" (HDA Intel - STAC92xx Analog)]**
** (pavucontrol:5737): DEBUG: blah: alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0
** (pavucontrol:5737): DEBUG: -5 = No such driver

**[For my "Virtual Output device" (Simultaneous output to HDA Intel - STAC92xx Analog)]**
** (pavucontrol:5737): DEBUG: blah: combined
** (pavucontrol:5737): DEBUG: -5 = No such driver

The question is: what does it mean? :confused:

Edit: I have no sound but the system beep is loud and clear (and cannot be muted with the Volume controller)!

---

