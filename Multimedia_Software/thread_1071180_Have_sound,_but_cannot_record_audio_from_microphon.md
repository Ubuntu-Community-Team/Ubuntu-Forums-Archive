---
title: "Have sound, but cannot record audio from microphone"
date: 2009-02-15
forum: Multimedia Software
---

### Post by lenards on 2009-02-15
I have audio from system sounds (at login), from audio apps (exaile, amarok, etc), and from dvd (totem, kaffeine).

But, I am unable to record sounds w/ Audacity nor Sound Recorder.

[{screenshot: sound preferences}]("http://gigism.com/sound_preferences.png")

My end goal is to be able to record audio and screen video with recordMyDesktop (I have jackd and qjackctl installed and they are running). 

The odd thing is that I have ALSA selected in all cases (System > Sound, Volume Control) but when I run `alsamixer` from command line it states that the card and driver are Pulse Audio. (all screenshots included at bottom)

[{screenshot: alsamixer}]("http://gigism.com/alsamixer.png")

The other odd thing is that in Volume Control, I've added the Capture track and when I click the microphone icon to active (get rid of the Red X), it goes away.  But, when I reopen - the Red X is back.  I thought LordRaiden's hints to help with saving your settings would help - but the above alsamixer issues mean that I don't have the capture tracks and such to attempt to modify. 

[{screenshot: volume control - recording tab}]("http://gigism.com/volume_control_recording_tab.png")
[{screenshot: volume control - playback tab}]("http://gigism.com/volume_control_playback_tab.png")

I've attempted the fix suggest here: [http://ubuntuforums.org/showthread.php?t=1069048]("http://ubuntuforums.org/showthread.php?t=1069048")

My OSS settings do not have a Front Mic, etc, as mentioned.  The approach didn't help the problem.


I'm running the following (included is `uname -a` output)

Ubuntu 8.10 Intrepid Ibex

Linux deedee 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

I've went through several troubleshooting guides and have not been able to get any sound recorded.  

Here's my asound info: 

> lenards@deedee:~$ more /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xb0000000 irq 22


> lenards@deedee:~$ more /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 0- 4]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 6]: digital audio playback
  8: [ 0- 6]: digital audio capture
  9: [ 0]   : control



> lenards@deedee:~$ cat /proc/asound/modules
 0 snd_hda_intel


Based on LordRaiden's guide, here's the output information:


> lenards@deedee:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



> 
lenards@deedee:~$ lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Uniwill Computer Corp Device 9077
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel



> lenards@deedee:~$ grep 'audio' /etc/group
audio : x : 29 : lenards,pulse


(note - spaces added to output to avoid smilies)

Screenshots: 

[sound preferences]("http://gigism.com/sound_preferences.png")
[alsamixer]("http://gigism.com/alsamixer.png")
[volume control - recording tab]("http://gigism.com/volume_control_recording_tab.png")
[volume control - playback tab]("http://gigism.com/volume_control_playback_tab.png")

---

### Post by lenards on 2009-02-16
My laptop is a dual boot setup.  I booted into Windows and was able to record sound with the headset I'm using w/ Audacity and the general sound recorder.  

Still not able to record in Ubuntu.

---

### Post by lenards on 2009-02-16
Note - in Audacity my playback & recording devices are: 

ALSA: HDA Intel: ALC880 Analog (hw:0,0)

I ran gnome-sound-recorder from the terminal and got the following output; 

> 
lenards@deedee:~$ gnome-sound-recorder

(gnome-sound-recorder:6241): GStreamer-CRITICAL **: gst_implements_interface_cast: assertion `gst_element_implements_interface (GST_ELEMENT (from), iface_type)' failed

(gnome-sound-recorder:6241): Gtk-CRITICAL **: gtk_widget_get_accessible: assertion `GTK_IS_WIDGET (widget)' failed

** (gnome-sound-recorder:6241): CRITICAL **: atk_object_add_relationship: assertion `ATK_IS_OBJECT (target)' failed
/tmp/gsr-record-Untitled-6241.G3BIPU
(gnome-sound-recorder:6241): GStreamer-CRITICAL **: gst_implements_interface_cast: assertion `gst_element_implements_interface (GST_ELEMENT (from), iface_type)' failed
/tmp/gsr-record-Untitled-6241.G3BIPU
(gnome-sound-recorder:6241): GStreamer-CRITICAL **: gst_implements_interface_cast: assertion `gst_element_implements_interface (GST_ELEMENT (from), iface_type)' failed
/tmp/gsr-record-Untitled-6241.G3BIPU


---

### Post by lenards on 2009-02-16
Nevermind the gnome-sound-recorder output.  That's an upstream problem and fixed in Jaunty. 

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/285208]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/285208")

---

### Post by lenards on 2009-02-17
> **lenards said:**
> 
The odd thing is that I have ALSA selected in all cases (System > Sound, Volume Control) but when I run `alsamixer` from command line it states that the card and driver are Pulse Audio. (all screenshots included at bottom)

[{screenshot: alsamixer}]("http://gigism.com/alsamixer.png")


I posted about [this issue]("http://ubuntuforums.org/showthread.php?p=6753178"), alsamixer reporting 'PulseAudio', and thanks to Reeman.  So running `alsamixer -c 0`, it reports the correct card/chip for my laptop. 

[http://ubuntuforums.org/showthread.php?p=6753178](http://ubuntuforums.org/showthread.php?p=6753178)

---

### Post by lenards on 2009-02-17
I got fresh drivers re LordRaiden's sticky guide (`sudo apt-get --purge remove ...`) and that's not helped one bit.  

I'm curious if I should start over w/ the steps of getting the problem nailed down. 

Any help or suggestions would be appreciate... I've exhausted most of my options.

---

### Post by lenards on 2009-02-18
I'm considering a downgrade to Hardy or Gutsy (to avoid PulseAudio)... or moving to XUbuntu, are Xubuntu users having the same microphone issues? 

It seems the I'm in good company when it comes the microphone not working in Intrepid. 

[LIST]
[*] [http://ubuntuforums.org/showthread.php?t=1006163]("http://ubuntuforums.org/showthread.php?t=1006163")
[*] [http://ubuntuforums.org/showthread.php?t=968056]("http://ubuntuforums.org/showthread.php?t=968056")
[*] [And the list goes on...]("http://www.google.com/search?q=ubuntu+intrepid+microphone&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial")
[/LIST]

---

### Post by lenards on 2009-02-18
nevermind on the Xubuntu thought: 

[http://ubuntuforums.org/showthread.php?t=1010579]("http://ubuntuforums.org/showthread.php?t=1010579")

---

### Post by keyboardslave on 2009-02-18
jan 2009 my mic isnt working eather exact same issues as u, ubuntu 10.8

---

### Post by lenards on 2009-02-18
I really can't explain my frustration with this issue...

---

### Post by lenards on 2009-02-18
To restate my goal: I need to capture audio and video on a linux machine. 

I cannot find a solution for my laptop's hardware with a ubuntu install.  So I'm running a guest ubuntu virtual machine using Sun'x xVM VirtualBox and capturing audio and video with the working windows sound card drivers.  

I don't know if virtualizing is an option for some of the people having hardware driver installs, but maybe that's an option. 

I know this isn't a solution to my original issue - but I've achieved my goal.

---

### Post by keyboardslave on 2009-02-18
Ok try this here on this post, i got it working perfectly,
[http://ubuntuforums.org/showthread.php?p=6759554](http://ubuntuforums.org/showthread.php?p=6759554)

Hope it helps mate.

---

